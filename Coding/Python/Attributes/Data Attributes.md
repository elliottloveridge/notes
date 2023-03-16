# Data Attributes

## What are Data Attributes
- Data attributes (instance variables) are variables belonging to a class
	- `self.variable`

## Non-Public Attributes
- Attributes whose name starts with a single underscore are for internal use only
	- Internal to the class object
- If you have attributes that should not be edited by a user you can refactor these
	- Add an underscore before the variable name
		- `_private_attribute`
	- There is a shortcut for doing this in the `__init__` method

- This is a rule that is used in Python but not explicitly defined
	- This is why they are known as non-public and *not* private attributes
	- You could in reality access them
- Python philosophy is **do not** hide attributes unless it would break the code
	- If you want to add an underscore then use *Rename Symbol (F2)* in Visual Studio
		- This won't fix occurrences in `__str__` method (see below snippet)
			- Requires regular expressions
				- `cmd + r` and tick regex in Visual Studio

```python
class Class:

	def __init__(self, name):
		# You can rename name to _name using 'rename symbol'
		self._name = name

	def __str__:
		# 'rename symbol' would not work for a reference within a string format
		return "{0.name}.format(self)"
```


### Mangling
- [[Subclasses#Mangling|Mangling]] is used for sub-classes
	- Double underscore prevents updating an attribute because of this
- - It isn't worth using this double underscore to try and enforce private attributes as even this can be ignored
- In Java, you can use inflection to read and write to private variables