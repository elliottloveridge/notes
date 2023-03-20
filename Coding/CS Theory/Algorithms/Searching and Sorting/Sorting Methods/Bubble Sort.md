# Bubble Sort

- Bubble sort is a simple, **inefficient** sorting algorithm used to sort lists
- The bubble sort algorithm **compares each pair of elements in an array** and swaps them if they are out of order until the entire array is sorted
- It has an average and worst-case time complexity of $\mathcal{O}(n^2)$
	- It has a best case of $O(n)$ for already sorted lists
- It does not have many practical uses due to its time complexity
	- One pro is that it only uses adjacent space (not auxiliary space) if this was a requirement
- It is a [[Stability|stable]] algorithm

- It works as follows;
	- Compare $A[0]$ and $A[1]$
		- If $A[0] > A[1]$, swap the elements
	- Move to the next element, $A[1]$ (this may now contain the result of a swap from a previous step), and compare it with $A[2]$
		- If $A[1] > A[2]$, swap the elements
		- Do this for every pair until the end of the list
	- Do steps 1 and 2 $n$ times

![[bubble-sort.png]]

## Complexity
- To calculate complexity it is useful to determine how many comparisons each loop performs
	- For each element, bubble sort does $n - 1$ comparisons - $\mathcal{O}(n)$
	- As there are $\mathcal{O}(n)$ operations performed on $\mathcal{O}(n)$ elements, leading to a running time of $\mathcal{O}(n^2)$
	- Like with [[Insertion Sort]], $\mathcal{O}(n)$ is the best-case runtime

## Implementation
```python
def bubble_sort(l):
    n = len(l) - 1
    for i in range(n):
        for j in range(n - i):
            if l[j] > l[j + 1]:
                l[j], l[j + 1] = l[j + 1], l[j]

    return l
```

- This can be optimised by breaking out of the loop if, after passing through the full list on the nth time, there were no swaps

```python
def bubble_sort(l):
    n = len(l) - 1
    for i in range(n):
        swapped = False
        for j in range(n - i):
            if l[j] > l[j + 1]:
                l[j], l[j + 1] = l[j + 1], l[j]
                swapped = True
        # Check if list is sorted before end of loop
        if not swapped:
            return l

    return l
```

