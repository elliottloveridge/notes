# Variables

- Variables are a way to store information in a computer
- Variables that we define can be accessed by a name we give them, and the computer does the hard work of figuring out where they get stored in the computers RAM
- As the name suggests, the contents of a variable can be changed
- There are lots of different types of data we can define for our variables
	- Collectively these are known as *data [[Types]]*

```java
int myFirstNumber = 5;
```

Expression - a construct that evaluates to a single value.

String Literal - unlike a variable, a String literal in Java cannot be changed.

Java operators (or simply, operators) perform an operation on a variable or values. +, -, /, and * are four common operators.

## Variable declarations
- To define a variable we need to specify the data type and give our variable a name
	- Optionally, add an expression to initialise the variable with a value
- Doing so is called a **declaration statement**

- To declare an uninitialised variable you can use;
```java
int x;
int y;
```

- This is valid within Java, allowing you to create the variables without a default value
	- In C, no default value is ever provided
- For Java;
	- Instance variables are given a default value of 0,
	- Or an explicit error is given for using a local variable before initialising it

## Assignment Statements
- `=` is assignment (not equality) of the right hand expression to the left hand variable
```java
int x = 4;
int y = 6;
int z = y - x;
```
