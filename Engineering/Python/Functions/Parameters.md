
# Function Parameters

## Defining Different Parameter Types
- This is an example of [[Engineering/Python/Functions/Functions|function]] parameters
```python
# Here, k is a keyword argument (otherwise it would have to be defined before *args)
def func(p1, p2, *args, k, **kwargs):
	print("positional-or-keyword:...{}, {}".format(p1, p2))
	print("var-positional (*args):..{}".format(args))
	print("keyword:.................{}".format(k))
	print("var-keyword:.............{}".format(kwargs))


# If you removed 'k=', then it would not know how to define this (passes 6 to *args)
func(1, 2, 3, 4, 5, k=6, key1=7, key2=8)
```

## Positional and Keyword Arguments
- You can define a default value for function parameters
```python
def some_function(foo, bar=None):
```
- `foo` is a positional argument
	- Any positional arguments need to be defined before keyword arguments
- `bar` is a keyword argument

### Positional Only
```python
def some_function(pos_only_1, pos_only_2, /, pos_or_keyword):
```
- You can define positional only arguments if they precede a `/`
	- You would use them if writing your own API

### Keyword Only
```python
def some_function(arg, *, kw_only_1, kw_only_2):
```
- You can define keyword only arguments if they follow a `*`

## \*Args
-  Mainly used within a function definition
	- Can be useful in other places
- A `*` before an object unpacks the sequence

```python
numbers = (0, 1, 2, 3, 4, 5)
# The print function effectively received print(0, 1, 2, 3, 4, 5)
print(*numbers)
```

- \*Args are useful when used in the reverse way
	- Specify a parameter as an unpacked sequence

```python
def test_star(*args):
	print(args)
	for x in args:
		print(x)

# Args is stored as a tuple of values here - you could also pass zero arguments (empty tuple)
test_star(0, 1, 2, 3, 4, 5)
```

## Kwargs