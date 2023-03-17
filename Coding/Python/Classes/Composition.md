# Composition

- Composition is when you define a class instance object as an instance variable of another class
	- The class is therefore composed of other classes and has no (or few) attributes of its own

```python
class Wing:

    def __init__(self, ratio):
        self.ratio = ratio

    def fly(self):
        if self.ratio > 1:
            print("I can fly")
        elif self.ratio == 1:
            print("This is hard work")
        else:
            print("I'll just walk")


class Duck:

    def __init__(self):
        # Example of composition (class instance as instance variable)
        # The class is composed of other classes and has no attributes of its own
        self._wing = Wing(1.8)

    def fly(self):
        self._wing.fly()
```
