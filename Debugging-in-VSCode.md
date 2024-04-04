VS Code is a very powerful tool to write code in but most developers I have seen debug are usually using the browser developer tools. VS Code has a very customizable and versatile debugging experience. I’m going to take a dive into showing how to successfully use and customize your debugger to get it working for your front-end projects.

The debugging menu can be brought up using the Run and Debug menu item in the GUI or if you like hotkeys you can use ⇧⌘D. This menu gives you a couple of GUI options but  the most impressive part is using a JSON to customize your debugging experience. By clicking the create a JSON file that is used to debug. On the bottom right of the window it will show a add configurations button that can help you fill out your JSON.

In the configurations array they’re are certain properties you want to add. The name key is what you are testing for, and this could be whatever name you want to give it, but remember be kind to your future self and be descriptive. The next is going to be key will be type, for most front end testing you will give it chrome. Then you will give the property of request to launch and this will launch the project. The next key/value pair is url and address of your locally ran live server address. Finally you will add webRoot with the key of ${workspaceFolder}, this will let VS Code know where you are working. All send and done will look like this:




```
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Debugging",
      "type": "chrome",
      "request":  "launch",
      "url": "http://127.0.0.1:5500/index.html",
      "webRoot": "${workspaceFolder}"
    }
  ]
}

```



Now you will have access to the configuration in the dropdown menu in the debugger. Once you run that debugger instance it will open a new instance of Chrome with your project. Now to the left of your individual lines of code you can add breakpoints and it will stop the code as its running at whatever line you add a breakpoint. Once a breakpoint is activated you can use the top right buttons to navigate your code. You have Continue/ pause, Step over, step into, step out, restart, and stop. 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/mnqvhswx0bwn0zjbek96.png)
	Once you’re at this point you can do some other nifty things. If you hover over variables you can see its value, you can also add variables to the watch tab to keep track of variable’s value as your code executes. With the variables tab you can see what variables are available in the respective scope. The call stack tab will give you insight on what your current call stack looks like.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/qaxqn1qdxmr2rdblqxll.png)
Hopefully now that you have a little peek at what VS Code's debugger is capable of you will want to take a deeper dive on your own and really understand the capabilities of the debugger. For more information I suggest going to the [Official Microsoft] (https://code.visualstudio.com/Docs/editor/debugging) documentation on the debugger and understanding the configurations that can be added to the launch.json file can do.