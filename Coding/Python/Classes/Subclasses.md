# Subclasses

## About Subclasses
- A subclass is a class that uses [[Inheritance|inheritance]] from a base class (superclass)

## Defining Subclasses
- You should define a constructor (`__init__` method) for a subclass but don't have to
	- You can still pass arguments to the superclass
	- If you define an `__init__` method in the subclass then Python will no longer look for the `__init__` method of the base class
		- You need to call it from within the subclass (see [[Super Methods|super methods]])

```python
# Define Enemy base class
class Enemy:

	def __init__(self, name="Enemy", hit_points=0, lives=1):
		self.name = name
		self.hit_points = hit_points
		self.lives = lives

	def take_damage(self, damage):
		remaining_points = self.hit_points - damage
		if remaining_points >= 0:
			self.hit_points = remaining_points
			print("I took {} points damage and have {} left".format(damage, self.hit_points))
		else:
			self.lives -= 1

	def __str__(self):
		return "Name: {0.name}, Lives: {0.lives}, Hit Points: {0.hit_points}".format(self)


# Define Troll subclass of Enemy
class Troll(Enemy):
	pass
```

## Overriding Methods
- Overriding methods allow you to modify the logic of the superclass method within a given subclass
	- You use the same method definition in the subclass
	- In the example below it would make sense to use [[Data Attributes#Non-Public Attributes|non-public attributes]] for the superclass (Enemy) definition

```python
# Define a subclass Vampire of superclass Enemy
class Vampire(Enemy):

	def __init__(self, name):
		super().__init__(name=name, lives=3, hit_points=12)
	
	# Create a new subclass method for dodging
	def dodges(self):
		if random.randint(1, 3) == 3:
			print("{0.name} dodges".format(self))
			return True
		else:
			return False
	
	# Create an overriding method of the superclass
	def take_damage(self, damage):
		if not self.dodges():
			super().take_damage(damage=damage)
```

## Mangling
- [[Data Attributes#Non-Public Attributes|Non-public attributes]] use a single `_` to denote being internal to a class
- Mangling is used to prevent accidental shadowing of attributes when creating sub-classes
- Two underscores is for subclassing
	- If you were to try and update an attribute that started with two underscores outside of the class it would not work
	- If it also ends with two underscores then it is not mangled
		- e.g. `__dict__`