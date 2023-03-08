# Type Hints
- Useful in large applications

## Function Annotations
- A special case of type hints applied to function parameters and returned values
- `def fibonacci(n: int) -> int:`
	- Defined the input parameter type and the return parameter type

### Default Value Annotations
- Normally for a default value you would not add spaces between the `=` sign
	- `def banner_text(text=" ", screen_width=80) -> None:`
		- No spaces between parameter name and default value
- For default value annotations you use spaces
	- `def banner_text(text: str = " ", screen_width: int = 80) -> None:`
- Used `-> None` as not returning a value