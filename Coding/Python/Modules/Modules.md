# Modules

### What is a Module?
- A module is a file containing Python definitions and statements
	- The file name is the module name + '.py'
- Modules can be imported into other modules
- Some modules can be run as a Python script in the command line
	- [[Useful Modules#Webbrowser|webbrowser]] is an example of this

### Importing Modules
- In order to use a module you need to import it
	- You should not use `from module import *`
		- You do not know what is being imported
		- May overwrite local functions/variables

#### Import Warnings
- Some import warnings are bugs
	- 'Unable to resolve module/function import' even if the module import is working
	- See [[Warnings#Suppressing Warnings|suppressing warnings]] to resolve this issue

