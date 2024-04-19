# C# from a Frontend Developer

This post is for developers looking to build something using C# and to document things I learned along the way. For work I was tasked with buildng a worker service for a windows server. Before this I only had expreience with building things for the web using Javascript, Typescript andsome of the more popular frameworks. So I had a very barebones undersatnding of how OOP (object oriented programming). I know everything in JS is an object but I was not prepared for OOP, but I learned alot and gained a lot of insight of some capabilities that JS has that admitedly isn't usually my programming style of programming, but this blog isnt about that. This is a post about something differnces I learnedon building a service worker.

## What I built with C#

Since I built this for work I cant get too detailed on what I build but the project is a worker service meant to run on an EC2 windows server. A worker service is a background process meant to run in the background on the server with no GUI. The program connects to APIs, a Database and has the ability to email, thats about as deep as I can get with it. This blog is less about how to replicate on what I built but rather somethings I learned along the way.

## Project Organization

The way I set up the project is set up all my classes that had methods in a folder called controllers. Each file was class that was set with tasks that were realated to the envs that needed to be passed in the contructor or methods that we're similar. So I had one that connected to the DB, APIs and email service. Another folder for the types that we're being recived from the api or being passed around in the project. There is a `StartAsync` where I set up the class objects setting up the constrictors for the classes and then in the `ExecuteAsync` method runs and that is where I am calling methods in the order that is needed.

## ENVs

This was a lot harder to understand how this works considering there are more than one way to pass envirinment variables. I found a lot of ways to pass variables into the project but the way I did it was in the `appsettings.json` file I made a section for config and created a object with all my keys. Which is really nice because you can organize your envs. So in the end it looked something like this:

```javascript
config: {
  test: {
    userName: "foo",
    password: "bar"
  }
}
```

Since C# is a strongly typed langauage. You have to set the model for the object. Now we're set to move forward. In main you can pass your json into the project from the hostbuilder. this is going to look something like this:

```C
...
    var host = new HostBuilder()
        .ConfigureAppConfiguration((hostContext, config) =>
        {
            config.SetBasePath(AppDomain.CurrentDomain.BaseDirectory)
                .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true);
...
```

Now we can grab our config section in out `appsettings.json`. This is done the worker in program.cs will run and we can pass dependencies for the project to use. Now you can pass the section you're looking for like this:

```C
_config = configuration.GetSection("config").Get<Config>();
```

Admitedly this is a lot of setup but with all this setup you can keep all your envs very clean and easy to reach. When you pass the `_config` object around you can target specfic parts of it as if it were an object using dot syntax: `_config.test.userName` because of the type return within the carats of the get method you can use that syntax.

## The Class

Classes have to major parts the constructor and the methods. The contructor is not always nessacry for a class but it is a feature. Here you can pass in dependencies like other classes and envs, that can be refernced from the methods. Somthing like calls to the DB or login creds to connect to the api can be used from the method that are setup in the constructor. This looks something like this:

```C
public class FOO{

  private string _foo;

  public FOO(string bar)
  {
      _foo = bar;
  }

  public bar(){
      Console.WriteLine(_foo);
  }
}
```

Call the method here with out setting up the construcor will give you an error or more likely not let you build your project with out failure. Once you have that set up you can call your method `FOO.bar()`. This concept can be really useful maintain really dry and clean code. Now that the setup of the class is done you would use it like this:

```C
FOO _foobar = new FOO("Hello World!")
_foobar.bar() // prints "Hello World!"
```

The first part of setting up that class is the type of the variable youre calling in the case of `_foobar` the type is `FOO`. Then you setup the constructor on the class. Then the method is called that refernces the private variable that is setup from the constuctor in the class. There will be some cases that a constructor is not needed and then you can just call methods that your need .

### The Overflow

Sometimes you will need to pass a differnt type into the method but you still want the same results. Like in the example above you might want to pass a number in to the contructor but want it to print in the console either way. You can use an overflow constructor in this case. Using the example above you would create another constuctor and setting up the class would infer from the useage. The overflow would looks something like this:

```C
public FOO(number num)
{
    _foo = num.ToString();
}
```

This can be done one methods as well as the constructor. This is useful if you want to pass in differnt parameters but still do alot of the same tasks. The pattern is great at keeping things dry.

## Nugget

Nugget is the package manager for C#. If you're using Visual Studio you can add and browse packages within a GUI which is nice if you dont know what youre looking for, if you do its really easy to install packages from the terminal. Somethings I found I needed for my purpose was the database package and JSON de/serializer along with withe built in packages within C#. To import these packages you use the keyword `using`, this is done at the top of the file that is being use in.

## FIN

This project was built with in a month on a rush for a client and with little or no expience in C#, .Net or OOP for that matter, I could have posibly gotten somethings wrong and if you're reading this and screaming into your monitor, [email](mailto:blog@codingMustache.dev) me and help me become a better programmer, I'm always ready to learn and upskill. You can use all caps if it makes you feel better. If this helped you feel free to email me and let me know too. I learned alot during this project and it made me more open to take on projects I wouldn't have before.
