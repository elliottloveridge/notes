# Methods

- Methods are functions that are inside of [[Coding/Java/Syntax/Classes]]
	- A method is a collection of statements that performs an operation
- In Java, everything is inside of a class, so technically all functions in Java are methods
- A **code block** is used to define a piece of code
	- It's mandatory to have one in a method declaration and it's here where you'll add statements to perform certain tasks

## Static Methods
- These behave a little differently from regular methods
- They don't act on any particular instance of a [[Coding/Java/Syntax/Classes|class]], they just belong to the class in general

### Main Method
- **main** is a special type of method that Java looks for when running a program
	- The entry point of any Java code

```java
public class Hello {

	public static void main(String[] args) {
		System.out.println("Hello World");
	}

}
```

- The left and right brackets after main are mandatory and can optionally include one or more parameters that pass information to a method

## Method Calls
- Method calls work a lot like function calls, except that we have to pass the *this* parameter to let the method know which object it is working on
	- e.g., `p1.distance(p2)`
		- Here, the *this* parameter points to `p1` with `p2` explicitly passed to it