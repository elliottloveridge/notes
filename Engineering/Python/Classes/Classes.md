# Classes
## About Classes
- Classes are used within [[OOP|OOP]]
	- You can think of a class as a template from which objects can be created
		- You create an *instance* of a class
			- Create an object of that class
			- This is also known as instantiation
	- An object constructor
- All objects created using a class will have the same characteristics
- Classes are made up of [[Engineering/Python/Methods/Methods|methods]] (functions) that act on that class object
### Data Attributes
- Variables bound to an instance of a class are known as data attributes
	- Also known as instance variables
	- Equivalent to fields in Java
#### Creating Attributes
- It is possible to add attributes outside of the class declaration (not recommended)
	- `class_object.new_variable = ...`
#### Printing Attributes
- You can reference attributes within print formatting
```python
print("Example: {0.attribute_name_1}, {0.attribute_name_2}".format(class_name))
```
## Self
- `self` is the name of a parameter
	- although the convention is to use the name self, the importance is actually what it is (and not what it is called)
- `self` is a *reference* to the instance of the class
## Circular references
- Say you had a class for Artist, Album and Song
	- You would not need to define an artist attribute within Song, Album and Artist
	- It is enough to define it in Artist and they will connect via standard flow
		- Artist $\rightarrow$ Album $\rightarrow$ Song
## Formatting
- Single line between method definitions
	- Also use a single line after the class definition
### Class Attributes
- Sub-classing
	- Where new classes are created from an existing one
		- Preferable to introducing new instance variables
- You can create a class such that additional variables may not be defined
- You can add class attributes (vs instance attributes) as normal variable definitions above the method declarations within a class declaration
- `class_instance.__dict__` returns a dictionary of attributes