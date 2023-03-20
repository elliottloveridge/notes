# Sorting

- There are two methods for sorting in Python
	- `.sort()` and `.sorted()`
- Both of these methods use TimSort
	- A hybrid algorithm that uses [[Merge Sort]] and [[Insertion Sort]] initially
	- $O(n\log{n})$ time complexity

## .sort()
- `.sort()` only works for list containers
	- Modifies the list rather than creating a new list
	- Works as lists are mutable
- You can also sort string lists using a key
```python
# Sort by string length
def my_func(s):
	return len(s)

l = ['hello', 'hi', 'hi there']
l.sort(key=my_func)
```

### Sorting Custom Objects
- You are able to sort custom objects
	- Useful when class objects do not have a natural order
```python
# Sort by x values of class Point
class Point:

	def __init__(self, x, y):
		self.x = x
		self.y = y


def my_func(p):
	return p.x


l = [Point(1, 15), Point(3, 8), Point(10, 5)]
l.sort(key=my_func)
```

- You can also create a method to deal with this function directly
	- Useful when class objects have a natural order
```python
class Point:

	def __init__(self, x, y):
		self.x = x
		self.y = y

	# Create less than method for sorting
	def __lt__(self, other):
		return self.x < other.x


l = [Point(1, 15), Point(3, 8), Point(10, 5)]
l.sort()
```

- There is also an equal to (`__et__`) method

## Sorted
- `.sorted()` works for any iterable container
	- list, tuple, dictionary, string, set, etc
- returns a **list** (does not modify original container)
