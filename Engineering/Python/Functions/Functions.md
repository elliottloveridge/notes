# Functions

## Arguments
- Arguments provide the values for [[Parameters|function parameters]]
	- You define and name your parameters when you define the function
	- You then pass arguments when you call the function
	- You can provide default values for parameters

## Scope
- Function scope - parameter variables only exist inside the function
	- They are not available in the code outside the function
- You should generally separate functions that perform actions and functions that return a result
	- Doing both can be difficult to maintain
	- Functions should be self contained blocks of code that either perform some action or return
		- Functions that perform an action used to be called *procedures* but modern programming languages no longer make that distinction
			- Instead, in Python they return `None`
			- Languages like C and Java use `void` as the return type to indicate nothing is returned

## Attributes

### Docstrings
- [[Docstrings]] and [[Type Hints#Type Hints#Function Annotations|Function Annotations]] help to document what a function does
	- Type hints perform a similar job to function annotations but are used for variables in your main program