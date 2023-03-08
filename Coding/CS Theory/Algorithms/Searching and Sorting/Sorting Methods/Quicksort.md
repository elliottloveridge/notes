# Quicksort
Quicksort is a fast sorting algorithm that uses a #divide-and-conquer to sorting lists.
- ==Quicksort has a **very slow** worst-case runtime, but a fast average/best-case runtime==

Quicksort uses the following;
**Divide:**
1. Pick a pivot element, $A[q]$
2. Partition, or rearrange, the array into two subarrays: 
	1. $A[p, \text{...}, q - 1]$ such that all elements are $\lt A[q]$
	2. $A[q + 1, \text{...}, r]$ such that all elements are $\geq A[q]$
**Conquer:**
3. Sort both subarrays recursively with quicksort
**Combine:**
5. No work is needed to combine the arrays because they are already sorted

---

## Choosing a Pivot
Picking a good pivot is key for a fast implementation of quicksort; however, it is difficult to determine what a good pivot might be.
- The partitioning step takes time proportional to the number of elements being partitioned, so reducing the number of elements in each partition would give a faster runtime
	- The best-case pivot would divide the array into two equal parts
	- For an effective quicksort this number would ideally be the median (but this means the list would already be sorted)

Here are ways of choosing a pivot:
1. Select a random pivot
2. Select the leftmost or rightmost element as the pivot
3. Take the first, middle, and last value of the array, and choose the median of those three numbers as the pivot (median-of-three method)
4. Use a [[Median-Finding Algorithm|median-finding algorithm]] such as the median of medians algorithm

## Implementation
```python
def quickSort(arr):
    less = []
    pivotList = []
    more = []

    if len(arr) <= 1:
        return arr
    else:
        pivot = arr[0]
        for i in arr:
            if i < pivot:
                less.append(i)
            elif i > pivot:
                more.append(i)
            else:
                pivotList.append(i)
        less = quickSort(less)
        more = quickSort(more)
        return less + pivotList + more
```

