# Environments

- You can create a venv with the corresponding env files (e.g. activate) within your working directory
- Pip is the python package manager

## Dependencies
- `pip freeze > requirements.txt`

- If installing from a requirements.txt file from within your virtual environment then use the following:
- `pip install -r requirements.txt`
	- Pipenv is a way to combine this with creating a virtual environment
		- Useful because you can have development only packages installed
			- You could install pytest in here for example
- 1.2.1 = major.minor.patch_version