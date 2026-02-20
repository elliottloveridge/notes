# Jump Search

> Like [[Binary Search]], **Jump Search** is a searching algorithm for sorted arrays

- The basic idea is to check fewer elements (than [[Linear Search|linear search]]) by ==jumping ahead by fixed steps== or skipping some elements in place of searching all elements.
For example;
- suppose we have an array `arr[n]` of size $n$ and a block (to be jumped) of size $m$
- search at the indexes `arr[0]`, `arr[m]`, `arr[2m]`, `...`, `arr[km]` and so on
- once we find the interval $\text{arr}[km] \leq x \leq \text{arr}[(k+1)m]$;
	- perform a ==linear search== from the index $km \rightarrow (k+1)m$ to find the element x
### Optimal Block Size
- In the **worst case**, we have to do $\frac{n}{m}$ jumps
- if the last checked value is greater than the element to be searched for:
	- perform $m - 1$ comparisons more for linear search
	- therefore the total number of comparisons in the worst case will be $\frac{n}{m} + (m-1)$
		- the value of this function will be minimum for $m = \sqrt{n}$
		- ==therefore, the best step size is $m = \sqrt{n}$==
### Python Implementation
```python
import math 

def jumpSearch(arr, x, n):
	"""
	Python Implementation of Jump Search.
	"""
	
	# block/step size to be jumped - set as int value further down
	step = math.sqrt(n) 
	
	# Finding the block where element is present (if it is present) 
	prev = 0
	while arr[int(min(step, n)-1)] < x: 
		prev = step 
		step += math.sqrt(n) 
		if prev >= n: 
			return -1
	
	# Doing a linear search for x in 
	# block beginning with prev. 
	while arr[int(prev)] < x: 
		prev += 1
		
		# If we reached next block or end 
		# of array, element is not present. 
		if prev == min(step, n): 
			return -1
	
	# If element is found 
	if arr[int(prev)] == x: 
		return prev 
	
	return -1

# Driver code to test function 
arr = [ 0, 1, 1, 2, 3, 5, 8, 13, 21, 
	34, 55, 89, 144, 233, 377, 610 ] 
x = 55
n = len(arr) 

# Find the index of 'x' using Jump Search 
index = jumpSearch(arr, x, n) 

# Print the index where 'x' is located 
print("Number" , x, "is at index" ,"%.0f"%index) 
```