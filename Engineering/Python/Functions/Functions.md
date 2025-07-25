# Functions
## Best Practices
- Write modules with functions like a list of *TO* statements
	- *TO* perform A, we include B
	- *TO* perform B, we include C
	- `...`
- These individual functions should also sit at a single level of abstraction
	- Using AVT as an example, you wouldn't have one line that modifies the orchestrator logic and the next line updates an individual quote tag
## 🧮 Function Arguments and Outputs
- Arguments provide the values for [[Parameters|function parameters]]
	- You define and name your parameters when you define the function
	- You then pass arguments when you call the function
	- You can provide default values for parameters
### 🎛️ General Guidelines
- Avoid multiple input arguments
    - Exceptions exist when the function needs to generalise well to multiple inputs (e.g. in libraries like pandas)
        - If it can be defined as an instance variable, that is normally clearer
- Avoid single input argument functions (transformations) that use output arguments instead of returning the transformed value
#### ❌ Bad Example: Modifying Output Argument Directly
```python
def transform(out):
    # Modifies out directly
    out.append(" transformed")

my_list = ["original"]
transform(my_list)
print(my_list)  # Output: ['original', ' transformed']
```
#### ✅ Good Example: Returning the Transformed Value
```python
def transform(inp):
    # Modify inp and return it
    inp.append(" transformed")
    return inp

my_list = ["original"]
my_list = transform(my_list)
print(my_list)  # Output: ['original', ' transformed']
```
### 🚩 Flag Functions
- Avoid flag functions
    - These involve passing in a boolean that modifies the behaviour of the function
    - This is a sign the function is doing more than one thing
## Scope
- Function scope - parameter variables only exist inside the function
	- They are not available in the code outside the function
- You should generally separate functions that perform actions and functions that return a result
	- Doing both can be difficult to maintain
	- Functions should be self contained blocks of code that either perform some action or return
		- Functions that perform an action used to be called *procedures* but modern programming languages no longer make that distinction
			- Instead, in Python they return `None`
			- Languages like C and Java use `void` as the return type to indicate nothing is returned
## Attributes
### Docstrings
- [[Docstrings]] and [[Type Hints#Type Hints#Function Annotations|Function Annotations]] help to document what a function does
	- Type hints perform a similar job to function annotations but are used for variables in your main program
