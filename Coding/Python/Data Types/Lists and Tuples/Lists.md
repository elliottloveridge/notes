# Lists

- Lists (and tuples) are sequence types
	- You can use indexing to access individual items
- A list is a collection of items in Python (container)
	- Internally, it uses an [[Arrays|array]] data structure
- There are other containers
	- Tuple, dictionary, set
- The speciality of lists is random access
	- If you want to know the `ith` element in a list you can find it in constant time
- Lists are dynamically sized and can contain multiple data types
	- This is automatically taken care of efficiently

## Python Internal

- In Python, a list normally uses an [[Arrays|array]] as the underlying data structure
	- Items stored in contiguous (neighbouring) blocks in memory
		- This is the definition of an array
		- Means indexing is fast (constant time complexity, `O(1)`)
	- Using an array benefits from random access
		- Get the `ith` item
		- Also benefits from cache friendliness
			- Caching pre-fetches neighbouring blocks
- Every variable/member of a list is actually a reference
	- So an array (list) is an array of references
		- The list stores reference locations in memory
		- The items are stored in different memory locations
- Dynamic array
	- The array may contain extra contiguous blocks in memory so that this can happen faster in future
- Disadvantages
	- Insertion, deletion and sort are slow
		- Say you wanted to insert at index 0, you would need to remove all items by 1
			- Linear time complexity, `O(n)`
		- Set is unordered but would be faster for these operations

- Since Python lists are an array of references, setting the variable `l2` below is a reference to the original l1 list and they would both act on it
	- Slicing creates a new list in memory (seen for `l3`)
```python
l1 = [1, 2, 3]

# Creates a reference to list l1
l2 = l1

# Creates a new list in memory
l3 = l1[:]
```

### Dynamic Size
- Pre-allocate space (10 items) when creating a list
	- Isn't always 10, depends on versioning etc
- When this pre-allocated becomes full (you want to add an 11th item);
	- Allocate a new space of larger size (multiply by x)
	- Copy old space to new
	- Free up old space
- Append has constant time complexity (on average)
	- Pop is also constant time

## Indexing

```python
l = [1, 2, 3, 4, 5]
```

- `l[0] = l[-5] = 1`
- `l[1] = l[-4] = 2`
- `l[2] = l[-3] = 3`
- `l[3] = l[-2] = 4`
- `l[4] = l[-1] = 5`

## Slicing
- `l[start:stop:step]`
	- `start` is inclusive
	- `stop` is exclusive
```python
l = [1, 2, 3, 4, 5]

# Slicing: [1, 3, 5]
print(l[0:5:2])

# [4, 3, 2]
print(l[4:1:-1])
```

### Mutability
- Due to mutability of lists, the following code returns false
	- They are different objects when slicing
```python
l1 = [1, 2, 3, 4, 5]
l2 = l1[:]
# False
print(l1 in l2)
```

## Functions

### List Functions
```python
l = [1, 2, 3, 4, 5]

# Append: [1, 2, 3, 4, 5, 3]
l.append(3)

# Insert: [1, 15, 2, 3, 4, 5, 3]
l.insert(1, 15)

# In: True
print(15 in l)

# Count: 2
print(l.count(3))

# Index: 1 (first occurence only)
# Raises an error if item not present in list
print(l.index(15))

# Remove: [1, 2, 3, 4, 5, 3]
# Raises an error if item not present in list
l.remove(15)

# Pop: 3
# Pop returns the removed item (if you print it)
print(l.pop())

# Pop: 1
# You can also provide an index
print(l.pop(0))

# Del: [3, 4, 5]
# General purpose deletion (not list specific)
del l[0]

# Del: [5]
del l[0:1]
```

### General Functions
- Note: a lot of the below functions will only work for numeric values
	- Or at least all values having equivalent type
```python
l = [1, 2, 3, 4, 5]

# Max: 5
print(max(l))

# Min: 1
print(min(l))

# Sum: 15
print(sum(l))

# Reverse: [5, 4, 3, 2, 1]
l.reverse()

# Sort: [1, 2, 3, 4, 5]
# The sorted() function creates a new sorted list (does not sort l)
l.sort()
```
