# Dictionaries

## About Dictionaries
- Dictionaries and sets are **not** sequence types (unlike [[Lists|lists and tuples]])
- You'll also find a dictionary referred to as a mapping
	- Python `dict` is equivalent to a `HashMap` in Java

- Dictionaries are stored as key-value pairs
```python
vehicles = {
	'dream': 'Honda 250T',
	'roadster': 'BMW R1100'
}
```

## Order
- In earlier versions of Python, the keys of a dictionary were unordered
	- Print would change each time
	- Python 3.6 preserved the insertion order of dictionary keys
- Dictionaries do not have an append
	- `dict['new_key'] = 'new_value'`

## Using Dictionaries

### Updating Values
```python
vehicles['dream'] = 'new_value'
```

### Removing Items
- `del` method would cause an error if using an incorrect key
```python
del vehicles['dream']
```
- `pop` is more efficient
	- Still fails if the key does not exist
```python
vehicles.pop('roadster')
```
- The below method allows you to pass a default value if unsure on the existence of a key
	- You could also pass a string like "Not Found" to make more logical sense
```python
vehicles.pop('roadster', None)
```

### Getting Values
#### Indexing
- You can use the key directly to get the associated value
	- Key must match exactly - case sensitive
	- This would crash if given an incorrect key
		- Sometimes preferable for error handling
- Indexing is faster than using a `.get()` method

```python
print(vehicles['dream'])
```

#### Get
- Get method for dictionary (equivalent to above)
- This would return None rather than crash with a key error

```python
print(vehicles.get('dream'))
```

### Iterating
- Iterating over a dictionary returns keys by default
```python
for key in vehicles:
	print(key, vehicles[key], sep=', ')
```
- If you need the value then the following is a more efficient approach of the above
```python
for key, value in vehicles.items():
	print(key, value, sep= ', ')
```
