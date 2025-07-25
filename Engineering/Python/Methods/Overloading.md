# Overloading

- Overloading methods are seen in Java (not Python)
	- You can use optional named parameters in a superclass to get the same result
- When you create different versions of the same method for different parameter types
	- The compiler decides which one to use based on the type of parameter passed
- Java has multiple (essentially identical) print methods
	- One for each data type
	- Python takes a different approach
		- It doesn't care about what something is, it's only interested in how each thing behaves
		- It focuses on what something does without worrying about what type it is
		- This is related to [[Polymorphism|polymorphism]]

## Python Version
- Python does not have overloading methods
- You can use optional named parameters in the `__init__` method of the superclass to get a similar result
	- See below class instance definitions for an example of this

```python
# Default values of superclass Enemy
one = Troll()
# Optional parameter definitions for superclass Enemy attributes
# This is equivalent to method overloading
two = Troll("Ug", 18, 1)
three = Troll("Urg", 23)
```
