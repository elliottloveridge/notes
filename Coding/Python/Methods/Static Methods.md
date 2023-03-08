# Static Methods

## What is a Static Method
- Static methods are shared by all instances of a class
- They are useful functions that the class (public) methods would use
	- User should never call a static method
```python
class Example:

	@staticmethod
	def _static_method_example():
		pass

	def __init__(self, variable1=...):
		pass
```

## Calling Static Methods
- Static methods can be called from within other methods
	- `ClassName._static_method()`

## Formatting
- Use a single `_` at the start of the method name
	- Denotes that this method should not be used outside of the class
- Definitions should follow `@staticmethod`
- Static method definitions sit above the `__init__` method