# Coupling
- We say an object is tightly coupled to another object when it is **too** dependent on it
	- All objects depend on other objects, but a loosely coupled object doesn't know or care too much about the details of another object
	- *Loosely coupled objects are more flexible and can better handle change*
## Loose Coupling
- The [Observer Pattern](Observer%20Pattern.md) is an example of loose coupling
	- The only thing the subject knows about an observer is that it implements a certain interface (the Observer interface)
		- It doesn't need to know about the concrete class of the observer
	- You can add new observers at any time
		- This can be done at runtime
	- You never need to modify the subject to add new types of observers
		- You only need to implement the Observer interface in the given class and register as an observer
	- You can reuse subjects or observers independently of each other
	- Changes to either the subject or observer will not affect the other