# Class Methods
- Similar to a [[Static Methods|static method]], a class method can be called without initialising a class

```python
class Dog(Animal):

	def __init__(self, param):
		super.__init__(param)

	@classmethod
	def some_class_method(self):
		print('hello')

Dog.some_class_method()
```
