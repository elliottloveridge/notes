# Properties

- A property method is used in conjunction with [[Getters and Setters|getters and setters]] when defining a class with [[Data Attributes#Non-Public Attributes|non-public attributes]]
- The property method lets you define three methods and a variable
	- `fget`: provide a getter function
		- If you don't specify this but specify `fset` then it will be write-only
	- `fset`: provide a setter function
		- If you don't specify this it will be read-only
	- `fdel`: provide a function to delete the attribute
		- Useful if the property is a list, for example
	- `doc`: docstring to provide a description of the property

## Standard Format
- The standard format (not commonly used) allows you to create getters and setters separately from their property definition
```python
# Getter
def _get_lives(self):
	return self._lives

# Setter
def _set_lives(self, lives):
	self._lives = lives

# Property definition
lives = property(_get_lives, _set_lives)
```

- Although not required you could define the property as the following
	- `lives = property(fget=_get_lives, fset=_set_lives)`

## Decorators Format
- [[Decorators]] are more commonly used for defining both properties and getters and setters
- Below is an example of this for the score data attribute
## Alternate Syntax for Properties
- Uses decorators
	- Takes care of the property definition that you would otherwise have to write
	- People tend to prefer this

```python
class Player(object):

	def __init__(self, name):
		self.name = name
		# Underscore represents hidden variable (outside of Class)
		self._lives = 3
		self._level = 1
		self._score = 0
	
	# Underscore represents hidden getter method
	def _get_lives(self):
		return self._lives
	
	# Underscore represents hidden setter method
	def _set_lives(self, lives):
		if lives >= 0:
			self._lives = lives
		else:
			print("Lives cannot be negative")
			self._lives = 0
	
	# Define getter for level
	def _get_level(self):
		return self._level
	
	# Define setter for level
	def _set_level(self, level):
		if level > 0:
			delta = level - self._level
			self._score += delta * 1000
			self._level = level
		else:
			print("Level cannot be less than 1")

	# Create properties of data attributes
	lives = property(_get_lives, _set_lives)
	level = property(_get_level, _set_level)

	# Using a decorator to define a property and getter (alternate form)
	@property
	def score(self):
		return self._score

	# Using a decorator to define a setter
	@score.setter
	def score(self, score):
		self._score = score
		
	# Special method - string representation of the object
	def __str__(self):
		return "Name: {0.name}, Lives: {0.lives}, Level: {0.level}, Score: {0.score}".format(self)
```