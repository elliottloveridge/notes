# Python Setup

## Homebrew
- Used as a package/application manager

- `brew list`
	- Get list of all installed packages
- `brew cask list`
	- Get list of all installed casks
- `brew search`
	- Find out what applications are available for install via Homebrew
- `brew upgrade --cask`
	- Update all casked applications
- `brew update`
	- Update homebrew

## PyEnv
- Used to manage Python install
- `ls ~/.pyenv/versions`
	- List your installed versions of Python
- `pyenv uninstall 3.x.x`
	- Uninstall a particular Python version
	- You can also use `rm -rf ~/.pyenv/versions/3.x.x`
- `sudo rm -rf venv`
	- Remove a venv
		- You should use `pyenv uninstall venv` first
- `pyenv shell venv`
	- Activate the Python environment

### Guide
1. `brew update && brew upgrade pyenv`
	1. Get latest available Python versions
2. `pyenv install --list`
	1. See all available Python versions

## Virtual Env
- Create and manage Python virtual environments

### Guide
1. `cd ~/Environments`
2. `mkdir venv-name`
3. cd `venv-name`
4. `pyenv virtualenv 3.:.: venv-name`
	1. Create a virtual environment using a specific Python environment, giving it the name 'venv-name'
	2. You need to specify the Python environment directly, e.g. 3.8.1
5. `pyenv activate venv-name`

### Pip Freeze
- `pip freeze` can be used to create a requirements.txt install file
- `pip freeze > requirements.txt`
	- I save this under `~/.pyenv/versions/venv-name/`

### Activating Virtual Env
- `source ~/.pyenv/versions/venv-name/bin/activate`
	- For PyEnv you can also use this
		- `pyenv shell venv-name`

