# Variables

## Variable Scope

### Function Variables
- You are **not** able to reference function variables outside of the function
```python
def some_func(x):
	y = x + 1
	return y


# This will return an error - undefined variables
print(x, y)
```

### Global Variables
- You **are** able to reference a global variable within function scope
```python
global_variable = 5

def some_func(x):
	return x + global_variable
```

- It will work but is not recommended to redefine these variables with the same name within a function
	- Generally not the best idea, better to pass in as a parameter
```python
global_variable = 5

def some_func(x):
	global_variable = 2
	# Returns x + 2
	return x + global_variable
```

- Similarly, if you want to update a global_variable within a function you can do the below
```python
global_variable = 5

def some_func():
	global global_variable
	global_variable = 2


some_func()
# This will have a value of 2
print(global_variable)
```
