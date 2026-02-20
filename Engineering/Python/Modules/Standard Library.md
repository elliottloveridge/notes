# Standard Library

- The Python standard library contains all builtin classes and modules
	- Some standard methods are written in C
		- Generally the ones that provide access to system functionality

## Printing
- You can get a list of modules within a file by using `print(dir)`
- Core builtin modules are imported by default
	- `print(dir(__builtins__))`
		- Everything in Python is an object so this would contain `list` as an object

## Source
- If modules written in Python you can view the source code by using `cmd +` clicking the module at import
	- You can also use `help(module)` to get information or `help(module.function)`