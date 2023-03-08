# Bubble Sort

- Bubble sort is a simple, **inefficient** sorting algorithm used to sort lists
- ==It has an average and worst-case time complexity of $\mathcal{O}(n^2)$==

The bubble sort algorithm **compares each pair of elements in an array** and swaps them if they are out of order until the entire array is sorted.

It works as follows;
1. Compare $A[0]$ and $A[1]$. If $A[0] > A[1]$, swap the elements.
2. Move to the next element, $A[1]$ (this may now contain the result of a swap from a previous step), and compare it with $A[2]$. If $A[1] > A[2]$, swap the elements.
	- Do this for every pair until the end of the list
3. Do steps 1 and 2 $n$ times

![[bubble-sort.png]]

## Implementation
```python
def bubble_sort(array):
    index = len(array) - 1
    while index >= 0:
        for j in range(index):
            if array[j] > array[j+1]:
                array[j], array[j+1] = array[j+1], array[j]
        index -= 1
    return array
```

## Complexity
To calculate complexity it is useful to determine how many comparisons each loop performs.
- For each element, bubble sort does $n - 1$ comparisons - $\mathcal{O}(n)$
- As there are $\mathcal{O}(n)$ operations performed on $\mathcal{O}(n)$ elements, leading to a running time of $\mathcal{O}(n^2)$
- Like with [[Insertion Sort]], $\mathcal{O}(n)$ is the best-case runtime.