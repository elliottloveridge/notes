# Sub-Classes

## What is a Sub-Class?

## Mangling
- [[Data Attributes#Non-Public Attributes|Non-public attributes]] use a single `_` to denote being internal to a class
- Mangling is used to prevent accidental shadowing of attributes when creating sub-classes
- Two underscores is for sub-classing
	- If you were to try and update an attribute that started with two underscores outside of the class it would not work
	- If it also ends with two underscores then it is not mangled
		- e.g. `__dict__`