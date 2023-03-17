# Inheritance

## About Inheritance
- In Python, inheritance is used to inherit attributes (data and methods) from a base class in a [[Subclasses|subclass]]
	- Inheritance allows you to write code for a superclass without needing to duplicate it for a relevant subclass
- You can define a **base class** (or *superclass*) and then something that inherits from that to make it unique
	- You could have a base class of 'Bird' and each subclass (Eagle, for example) would inherit properties such as a beak or wings from the Bird class
	- The subclasses also inherit methods
		- An eagle would inherit walk and eat, for example, from the Bird class
- You could take this a level further with multiple inheritance and have Bird $\rightarrow$ Flying Bird $\rightarrow$ Eagle

- In Python, ultimately your base class is also a subclass as it inherits from a builtin class called Object
	- There is no need to specify this (`class ClassName(object):`)
		- This wasn't the case in Python 2

### Benefits
- Subclass get attributes (data and methods) from superclass to prevent duplicate code
- You are able to extend/alter superclass methods using [[Subclasses#Overriding Methods|overriding methods]]

## Multiple Inheritance
- In Python, classes can inherit directly from several superclasses
	- This is known as multiple inheritance
- You should avoid this in practice most of the time
	- Many languages don't allow this
		- You can have more than one superclass but it has to be hierarchical

```python
# Define Enemy superclass
class Enemy:

    def __init__(self, name="Enemy", hit_points=0, lives=1):
        self.name = name
        self.hit_points = hit_points
        self.lives = lives
        self.alive = True


# Define inheritance class
class Vampire(Enemy):

    def __init__(self, name):
        super().__init__(name=name, lives=3, hit_points=12)


# Define multiple inheritance
class VampireKing(Vampire):

    def __init__(self, name):
        super().__init__(name)
        self.hit_points = 140
    
    def take_damage(self, damage):
        super().take_damage(damage // 4)
```