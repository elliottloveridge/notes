# Functions

- Functions allow for a piece of code to be re-run without rewriting it, giving it a name and parameters
	- Technically speaking, Java has methods and not functions
		- It has methods since all code in Java is inside of objects
- Programs start from the *main* method - in the below example we assume you called function `g` first

## How a Function Works
- You create a *frame* to store function variables
	- This is 'destroyed' after the function has returned its value
- A **call site** is a note of where to return after the function call
	- i.e. to the line where the function was used
- **return** leaves the current function and returns to the call site
	- Copying the return value from the function
- When you call a function, you copy the assigned variables into the frame of the function call
	- For example, `a = myFunction(3, 7)` adds `x = 3` and `y = 7` into the frame of myFunction

```java
int myFunction(int x, int y) {
	int z = 2 * x - y;
	return z * x;
}
int f(int n) {
	return 3 + myFunction(n, n+1);
}
int g() {
	int a;
	a = myFunction(3, 7);
	int b = f(a * a);
	return b;
}
```