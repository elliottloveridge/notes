# Loops

## For Each Loop
- HelloWorld, seen below, does not have a constructor
	- In this case, Java provides a default constructor but with no arguments (does nothing)

```java
import edu.duke.FileResource;

public class HelloWorld {
	public void runHello() {
		// Declares the variable f
		FileResource f;
		// Initialise variable f as a FileResource object
		f = newFileResource("file.txt");
		// Declare a variable line for each in f.lines()
		for (String line : f.lines()) {
			System.out.println(line);
		}
	}

	// How to invoke the runHello method from main
	public static void main(String[] args) {
		// Creates a new HelloWorld object called hw
		HelloWorld hw = new HelloWorld();
		// Passes in hw as a this parameter (arrow) to runHello
		hw.runHello();
	}
}
```