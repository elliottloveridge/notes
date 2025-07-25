# Super Methods

- The super method is used to give access to data attributes and methods from a superclass
	- It is commonly used within the `__init__` of a [[Subclasses|subclass]]

## Calling Super Methods
- The `__init__` method of the subclass shadows the superclass `__init__` method
	- To get around this you call the superclass `__init__` method from within the subclass `__init__` method
		- This makes sure the class attributes are initialised (name, etc. below)

### Standard Format
```python
# Define Troll subclass of Enemy
class Troll(Enemy):

	def __init__(self, name):
		# Call the superclass init method
		Enemy.__init__(self, name=name, lives=1, hit_points=23)
```

### Super Method
- If you want to deal with multiple inheritance you need to use super instead of specifying the base class name
	- This is the **recommended** way in Python

#### Long Form
```python
# Define Troll subclass of Enemy
class Troll(Enemy):

	def __init__(self, name):
		# Use super to call the init method of the base class
		super(Troll, self).__init__(name=name, lives=1, hit_points=23)
```

#### Short Form
- the short form below is the preferred style most often used
	- The complier knows the type 'Troll' and the instance 'self'
		- No need to specify them in the super call
```python
def __init__(self, name):
	super().__init__(name=name, lives=1, hit_points=23)
```
