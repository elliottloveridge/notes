# Strategy Pattern
- The **Strategy Pattern** defines a family of algorithms, encapsulates each one, and makes them interchangeable
	- Strategy lets the algorithm vary independently from clients that use it
- For the below example, think of the behaviours as a family of algorithms
	- Quack, Speak, and NoQuack are the algorithms in this example
## Example
- Say you have a class Duck that has methods fly and quack
- What if you wanted to create a subclass of this, one for Mallard duck and one for a toy duck
- You wouldn't want them both to inherit the same quack and fly methods
	- A toy duck doesn't fly or quack!
### Bad Example
- One solution would be to create a class `Duck` and then have subclasses `Mallard` and `ToyDuck` override the super class methods `fly` and `quack`
- What's the problem with this?
	- Every time there is a change you will need to edit each subclasses override
		- Hard to keep track of and will likely cause bugs
### Good Example
- You take out flying and quacking as separate behaviours likely to change
- You create a FlyBehaviour superclass that has subclasses FlyWithWings, etc. (e.g., types of flight)
	- Do the same for QuackBehaviour
- The Duck superclass (and each individual subclass) do not need to know how this behaviour is implemented, they just use it
- The duck class would then have an instance variable fly_behaviour that is set to a subclass of FlyBehaviour
	- You can then have a perform_fly method within the Duck class
		- `fly_behaviour.fly()`

```python
class Duck:
    def __init__(self):
        # You could also have self.fly_behaviour = None
        self.fly_behaviour = FlyBehaviour()

    def set_fly_behaviour(self, fly_behaviour):
        self.fly_behaviour = fly_behaviour

    def perform_fly(self):
        self.fly_behaviour.fly()

    def display(self):
        raise NotImplementedError

    @staticmethod
    def perform_swim():
        print("All ducks float, even decoys!")


class MallardDuck(Duck):
    def __init__(self):
        super().__init__()
        self.fly_behaviour = FlyWithWings()

    def display(self):
        print("I'm a real Mallard duck!")


class ModelDuck(Duck):
    def __init__(self):
        super().__init__()
        self.fly_behaviour = FlyNoWay()

    def display(self):
        print("I'm a model duck")


class FlyBehaviour:
    def fly(self):
        raise NotImplementedError


class FlyWithWings(FlyBehaviour):
    def fly(self):
        print("I'm flying!")


class FlyNoWay(FlyBehaviour):
    def fly(self):
        print("I can't fly!")


mallard = MallardDuck()
mallard.perform_fly()

model = ModelDuck()
model.perform_fly()
model.set_fly_behaviour(FlyWithWings())
model.perform_fly()
```