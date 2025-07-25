# Methods
- A method is a function that is defined within a class
	- A function that acts on an object
## Special Methods

- `__new__` is the first method to be called when creating an instance of a class
	- Known as the **Class constructor** (takes care of creating the class)
		- You don't need to define this unless sub-classing
- `__init__` method
	- This then customises the class after the `__new__` method creates it
	- Variables in the method call are used to give value to attributes
		- `__init__(self, variable_1)`
## Method Calls
- The standard way to call a method after creating a class object instance is;
	- `class_object.method()`
	- The `self` reference is implicitly defined here
- You can also call a method without this reference (uncommon)
	- `Class.method(class_object)`