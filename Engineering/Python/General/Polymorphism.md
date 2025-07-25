# Polymorphism

- Polymorphism means having many forms
	- An object can be more than one thing at the same time
	- Python relies heavily upon this

## Example
- You can add two `int` types but not two `string` types
	- They are very different types of objects
	- However, they also share printable behaviour (you can print both in the same way)
		- They both behave like a printable object in that respect
- In the above example, the polymorphic behaviour of the objects is *implemented using [[Inheritance|inheritance]]*
	- All Python objects inherit from a base class called 'object' which defines a `__str__` method
		- Polymorphism allows the print function to accept arguments of any type
			- Because you inherit `__str__` from the base object, every defined object is guaranteed to have this property

- In both Python and Java, classes inherit from the topmost base class called object
	- This base class defines a basic implementation of the `__str__` method in Python
		- The default implementation of `__str__` isn't very pretty
			- It just returns the name of the class and a hash code or the address in memory where the object lives
		- Defines an equivalent `toString` method in Java

- Inheritance is not the only way to define polymorphism
	- You could define two classes with equivalent method names
	- They would therefore be considered equivalent in terms of calling methods
