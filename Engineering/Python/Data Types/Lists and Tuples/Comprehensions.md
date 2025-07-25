# Comprehensions

- A syntax shortcut to create a list from another iterable
	- Range, List, Tuple, Set, Dictionaries are all examples of iterables

## List Comprehension
```python
# Even numbers: [0, 2, 4, 6, 8]
l = [i for i in range(10) if i % 2 == 0]
```

## Dictionary Comprehension
```python
# Squared values
d = {x: x**2 for x in range(5)}

# Fstring values
d = {x: f'ID{x}' for x in range(5)}

# Using two lists
# # NOTE: there is a better way to do this (see below)
l1 = [0, 1, 2]
l2 = ['ID0', 'ID1', 'ID2']
d = {l1[i]: l2[i] for i in len(l1)}

# Zip
# Creates a collection of mappings (tuples)
d = {zip(l1, l2)}


```