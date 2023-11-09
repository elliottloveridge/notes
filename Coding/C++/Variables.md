# Variables
- Each variable in C++ (cpp) has a:
	- data type
	- name
	- value
- You must **declare** and assign a variable before you can access it
## Variable Types
### Int
```cpp
int number;
number = 50;
cout << number << endl;
```
- You can declare and assign a variable in a single line
	- `int number = 50;`
### Floating Point Numbers (Floats)
- In cpp there is a data type called float, but as it only uses 4 bytes, it is insufficient for most math
	- Instead, we use double which uses 8 bytes (**double** the space of a float)
```cpp
double decimal = 0.5;
```
### Boolean
- Can only take the value of `true` or `false`
- The below outputs `1` to the terminal
```cpp
bool myFlag = true;
cout << myFlag << endl;
```
### Strings
- A collection of text, numbers, or symbols
	- Always surrounded by quotation marks
```cpp
string words = "This is a string";
cout << words << endl;
```
## Declaring Variables
- Declaring a variable has two parts - setting the **type** and **name**
	- These two properties do not change
		- You **can** overwrite variable values
- Variables are case sensitive
	- Should be lower case and start with a letter or underscore
- You cannot overwrite cpp key words
	- Reserved for specific functions or tasks