# Docstrings

- Docstrings are a class/function attribute
	- Everything in Python is an object

## About Docstrings
- [Docstring guidelines](https://peps.python.org/pep-0257/)
- You can use `option + left-click` on a function to find that function
- Docstrings belong inside the function (or class)
	- They are an attribute of the function in Python
	- They become the `__doc__` special attribute of that object (e.g. function)
		- Everything in Python is an object
- Use `backticks` around any Python names that you refer to
- You can use `print(function.__doc__`)
	- You are not calling the function here, you are referring to one of its attributes
		- Hence you don't need to write `function().__doc__`
	- You can also just highlight over the function call to view the docstring

### Formatting
- Have an introductory line to describe the class/method and then a single space before giving more details (if needed)

### Raises
- You should document any raises within a function (e.g. ValueError) along with a reason for the raise