# Linear Search

- Given an array `arr[]` of $n$ elements, write a function to search for a given element $x$ in the array
- A **linear search** may be defined as;
	- Starting from the leftmost element of an array and one by one comparing $x$ with each element
	- If $x$ matches with an element, return the index
	- If $x$ doesn't match with any of the elements, return $-1$

## Time Complexity
- The time complexity of a linear search is $\mathcal{O}(n)$
	- This is because it searches the entire element space
	- Does not make use of the fact a given list may be sorted
- Linear search is rarely used practically because other search algorithms such as [[Binary Search|binary search]] and [[Hash Tables|hash tables]] allow for significantly faster searching

## Python Implementation
```python
def search(arr, n, x):
	
	for i in range(0, n):
		if (arr[i] == x):
			return i
	return -1


# Driver code
arr = [2, 3, 4, 10, 40]
x = 10
n = len(arr)

# Function call
result = search(arr, n, x)
if (result == -1):
	print("Element is not present in array")
else:
	print("Element is present at index", result)
```
