# Classes

- A class is a template that specifies how to make objects
- The **class** keyword is used to define a class with the name following the keyword. The curly braces after the class name define the class body ({})

```java
public class Hello {
}
```

## Example Class
```java
// A class that represents a 2D point

// Declare a class called Point
public class Point {
	// Declare two fields (instance variables), int x and int y
	// NB: Only code within the class Point can access private fields
	private int x;
	private int y;
	// Declare the constructor for the class
	public Point(int startx, int starty) {
		x = startx;
		y = starty;
	}
	// Declare methods
	public int getX() {
		return x;
	}
	public int getY() {
		return y;
	}
	public double distance(Point otherPt) {
		int dx = x - otherPt.getX();
		int dy = y - otherPt.getY();
		return Math.sqrt(dx * dx + dy * dy);
	}
	// Declare static method
	public static void main(String[] args) {
		Point p1 = new Point(3, 4);
		Point p2 = new Point(6, 8);
		System.out.println(p1.distance(p2));
	}
	
}
```

## Class Walkthrough

- [[Constructor]]
	- A constructor looks like a function but with no return value
		- It also has the same name as the class
	- In front of the constructor we have the word public which means that any code can use this constructor to create a point
	- Constructors and methods take an additional implicit parameter which tells them which object they are operating on
	- That parameter is called *this* and its value is an arrow which points to the object that it is acting on
- [[Engineering/Java/Syntax/Methods]]
	- After the constructor there are three methods; getX, getY, and distance
		- These methods are invoked or called on a particular object and implicitly act on that object
- [[Engineering/Java/Syntax/Methods#Static Methods|Static Methods]]
	- The method is called **main** which is a special method (the starting point)
