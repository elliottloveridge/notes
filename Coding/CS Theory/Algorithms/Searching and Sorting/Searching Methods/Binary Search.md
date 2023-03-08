# Binary Search

- Search a **sorted array** by repeatedly dividing the search interval in half.
- Begin with an interval covering the whole array
	- If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise narrow it to the upper half
	- Repeatedly check until the value is found or the interval is empty.

## Complexity
- You are reducing the search space by a factor of 2 each time, so the complexity is $\mathcal{O}(\log{n})$

### Python Implementation
```python
def binarySearch(arr, l, r, x):
	"""
	Recursive Binary Search.
	Returns index of x in arr if present, else -1.
	
	Args:
	arr: array to be searched
	l: index of leftmost element in arr
	r: index or rightmost element in arr
	x: element to search for
	
	"""

	# Check base case
	# if rightmost index is less than leftmost index then we have
	# searched the whole array and not found the number
	if r >= l: 

		mid = l + (r - l) // 2

		# If element is present at the middle itself 
		if arr[mid] == x: 
			return mid 
		
		# If element is smaller than mid, then it 
		# can only be present in left subarray 
		elif arr[mid] > x: 
			return binarySearch(arr, l, mid-1, x) 

		# Else the element can only be present 
		# in right subarray 
		else: 
			return binarySearch(arr, mid + 1, r, x) 

	else: 
		# Element is not present in the array 
		return -1


# Driver Code 
arr = [ 2, 3, 4, 10, 40 ] 
x = 10

# Function call 
result = binarySearch(arr, 0, len(arr)-1, x) 

if result != -1: 
	print ("Element is present at index % d" % result) 
else: 
	print ("Element is not present in array")
```

### C++ Implementation
```c++
// A recursive binary search function. It returns 
// location of x in given array arr[l..r] is present, 
// otherwise -1

#include <bits/stdc++.h> 
using namespace std; 

int binarySearch(int arr[], int l, int r, int x) 
{ 
	if (r >= l) { 
		int mid = l + (r - l) / 2; 

		// If the element is present at the middle 
		// itself 
		if (arr[mid] == x) 
			return mid; 

		// If element is smaller than mid, then 
		// it can only be present in left subarray 
		if (arr[mid] > x) 
			return binarySearch(arr, l, mid - 1, x); 

		// Else the element can only be present 
		// in right subarray 
		return binarySearch(arr, mid + 1, r, x); 
	} 

	// We reach here when element is not 
	// present in array 
	return -1; 
} 

int main(void) 
{ 
	int arr[] = { 2, 3, 4, 10, 40 }; 
	int x = 10; 
	int n = sizeof(arr) / sizeof(arr[0]); 
	int result = binarySearch(arr, 0, n - 1, x); 
	(result == -1) ? cout << "Element is not present in array"
				   : cout << "Element is present at index " << result; 
	return 0; 
} 
```

