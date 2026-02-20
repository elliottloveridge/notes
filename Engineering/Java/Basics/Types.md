# Types

- A type specifies how data should be represented, interpreted, operated on, as well as what operations you can do with it
- One important rule of computing is that everything is a number
	- They could mean;
		- Normal numbers
		- Letters
		- Locations of data in the computers memory
- Everything is stored in the computers memory as **bits**
- Type specifies how to interpret this in memory
	- Also what you can do and how it can be done

## Type Categories
### Primitives
- int
- double
- char
- boolean
- float
- long
- byte
- short

- For primitive types;
	- Value is held directly in their 'box'
	- Can't invoke methods on them
	- Can't be null (but can use wrapper class)

### Objects
- Some are built into Java
	- String
- Others are a part of libraries you might use
	- Point
	- FileResource
	- Classes you make yourself
		- Whenever you make a class, the class is its own new type

- For Object types;
	- Values of variables of Object types is a reference (arrow) to the object
	- Can invoke methods
	- Can access fields with dot
	- Can be null
	- `==` checks if arrows point at the same object

## Conversion Between Types
- Some types can be converted implicitly
```java
int x = 3;
// Implicit conversion
double d = x;
```
- Some types require an explicit cast
```java
double d = 3.14;
int x = (int)d;
```
- Others require method calls
```java
String s = "3";
int x = Integer.parseInt(s);
```