# Getters and Setters

- A *getter* is a method that retrieves a data attribute value
- A *setter* is a method that is used to set the value of a data attribute
- If all a getter/setter is doing is a basic get value and set value then it doesn't really need to be a property

- Python classes do not need getters and setters to read and change data attribute values
	- Don't use them when creating a standard class
		- You can add them to a class later on if you think you'll need one
- When defining getters and setters you should also define a **[[Properties|property]]**
	- This is most commonly done using a [[Decorators|decorator]]

- Below is an example of calling a getter and setter method from a class_instance
	- `lives` and `name` are encapsulated into a Class object
```python
# Example getter
print(class_instance.get_name())

# Example setter
class_instance.set_lives(300)
```

-  However, these attributes are **not hidden**
	- In Python, this is considered the way to do things (provide access to data attributes)
	- Opposite for Java, etc. which uses private instance variables
```python
# Import a class
from player import Player

# Create a class instance
tim = Player("Tim")

# Update a data attribute without the use of a setter (possible in Python)
tim.lives -= 1
```

## Definitions
- For the best way to define getters and setters see [[Properties#Decorators Format|decorators format]]

- Below is an example class that uses two methods of creating getters and setters
	- `_lives` uses [[Data Attributes#Non-Public Attributes|non-public attribute]] formatting
- When defining a getter/setter you should also include a [[Properties|property]] definition
- The `__str__` method lets you print out a class instance
	- `print(class_instance_name)`

```python
class Player(object):

	def __init__(self, name):
		self.name = name
		# Underscore represents non-public (hidden outside of the Class) variable 
		self._lives = 3
		self.level = 1
		self.score = 0
	
	# Underscore represents hidden getter method
	def _get_lives(self):
		return self._lives
	
	# Underscore represents hidden setter method
	def _set_lives(self, lives):
		self._lives = lives

	# Property definition
	lives = property(_get_lives, _set_lives)

    # Special method - string representation of the object
    def __str__(self):
        return "Lives: {0.lives}, Level: {0.level}, Score: {0.score}".format(self)
```

