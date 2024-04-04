 Released in 2014 a relatively new language by Apple and open source contributors. Is the language to develop for apple products, from the iPhone, to apple watch to OSX native apps. It is a complied programming language that replaced Objective-C. Though made to replace Objective-C, C, C++ and Objective-C can be compiled alongside with Swift because Xcode uses an Objective-C runtime library. Xcode is the definitive IDE to develop with using Swift. The main frameworks for Swift is Cocoa and Cocoa Touch. 

# Syntax
Some of the syntax is very similar to other modern languages like Javascript and Python. For Example writing a comments looks something like this:
```

  // this is a single-line comment 
  /*
  This is 
  A multi-line 
  Comment 
  */
  
```
And similar to Javascript semicolons are not required after each statement in your code but you can optionally use it. Which is very similar to the Javascript commenting syntax. And to do a simple hello program is very simple to Python syntax, looks like this:
```

  var str = “Hello World!”
  print(str)
  
```
If you add this to a REPL like codePen or Replit, congratulations you wrote your fists swift program. 

# Datatypes 
Swift is a type-safe language, that makes sure you can not reassign the variable to a different datatype by accident. It has 8 built in basic datatypes in swift:
Int: A whole number
Float: A 32-bit floating point number
Double: A 64-bit floating point number
Bool: A boolean, true or false
String: A collection of characters 
Character: A single string character 
Optional: A variable that can hold either a value or no value
Tuples: Used to group multiple values in a single compound value

# Variable Assignments
There are to ways to assign a variable is either using `var` or `let` keywords. Assigning a variable with var will give the variable ability to reassigned and the `let` will do the opposite of that and create a constant. Using the keywords looks like this:
```

  let pi = 3.4;
  var index = 1; 
  
```

# Operators

## Arithmetic Operator

There are some symbols you can use to do arithmetic operations between operands.
```

 + adds
 - subtracts
 * multiples 
 / divides 
 % remainder from dividing the operands
 
```
## Comparison Operators 
Comparison operator compares 2 operands and returns true or false:
```

 ==  Checks if operand from the left and right of the comparison are equal to each other
 !=  Checks of the operand are not equal to each other
 >  Checks if operand from the left is larger than the operand on the right 
 <  Checks if operand from the right is larger than the operand on the left
 <=  Checks if operand from the left is larger than the operand on the right or equal to
 >=  Checks if operand from the right is larger than the operand on the left or equal to
 
```
This is a simple pass over on the Swift programming language, there is a lot more to know like how to build loops methods and building functions... To get started on building your apple app, I urge you to take a look at the documentation [here](https://www.swift.org/). It is a very easy language to learn and has a great community in the Swift forums [here](https://forums.swift.org/), it's a great place to ask questions and learn a lot about the language.
 
