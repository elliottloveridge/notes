# Merge Sort
An efficient sorting algorithm that uses a #divide-and-conquer approach to order elements in an array.

- Mergesort runs in a guaranteed $\mathcal{O}(n\log{n})$ time

- The mergesort algorithm focuses on how to merge together two pre-sorted [[Arrays|arrays]] such that the resulting array is also sorted
- ==Mergesort can be implemented either recursively or iteratively==

### Recursive Mergesort
1. If the list only has one element, return the list and terminate (Base case)
2. Split the list into two halves that are as equal in length as possible (Divide)
3. Using recursion, sort both lists using mergesort (Conquer)
4. Merge the two sorted lists and return the result (Combine)

### The Merge Step
The purpose of the merge function is to merge two sorted lists such that the resulting list is also sorted

1. Create an empty result list
2. Do the following until one of the input lists is empty:
	- Remove the first element of the list that has a lesser first element and append it to the result list
3. When one of the lists is empty, append all elements of the other list to the result

### Complexity of the Merge Function

`this is not the full merge sort algorithms complexity, that is seen below`

- The merge function does a constant ($\mathcal{O}(1)$) number of operations for each element in the list
- The list size is $\mathcal{O}(n)$ since there are $n$ elements
- Therefore, ==mergesort occupies $\mathcal{O}(n)$ in time==

### Time Complexity of Merge Sort
**Division**
It takes $\mathcal{O}(1)$ time to divide the problem into two parts, computing only the middle of the length of the list (constant time)

**Solving the sub-problems**
Two equally large sub-problems are produced. Each takes $T(\frac{n}{2})$ time, so solving both takes a total of $2T(\frac{n}{2})$ time.

**Combining the sub-problems**
This is the merge step of the mergesort. This step takes $\mathcal{O}(n)$ time, as shown above for the merge function.

Therefore;

$$T(n) = 2T(\frac{n}{2}) + \mathcal{O}(n)$$

The [[Master Theorem|master theorem]] tells us that the solution to this recurrence is;

$$T(n) = \mathcal{O}(n\log{n})$$

==Mergesort runs in this time in its best case, worst case and average case==

### Implementation
```python
def merge(left, right):
    result = []
    left_idx, right_idx = 0, 0
    while left_idx < len(left) and right_idx < len(right):
        if left[left_idx] <= right[right_idx]:
            result.append(left[left_idx])
            left_idx += 1
        else:
            result.append(right[right_idx])
            right_idx += 1

    if left:
        result.extend(left[left_idx:])
    if right:
        result.extend(right[right_idx:])
    return result

def merge_sort(m):
    if len(m) <= 1:
        return m

    middle = len(m) // 2
    left = m[:middle]
    right = m[middle:]

    left = merge_sort(left)
    right = merge_sort(right)
    return list(merge(left, right))
```