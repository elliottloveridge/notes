## Insertion Sort

- A sorting algorithm that builds a final stored array one element at a time
- Insertion sort has an average and worst-case running time of $\mathcal{O}(n^2)$, so ==in most cases, a faster algorithm is more desirable==

For insertion sort you;
1. Compare the first two values of an array, placing them in order
2. Compare the third with the second and first, placing in order
3. Loop this until sorted

![[insertion-sort.png]]

### Implementation
```python
def insertion_sort(array):
    for slot in range(1, len(array)): 
        value = array[slot]
        test_slot = slot - 1
        while test_slot > -1 and array[test_slot] > value:
            array[test_slot + 1] = array[test_slot]
            test_slot = test_slot - 1
        array[test_slot + 1] = value
    return array
```

### Complexity
**Best Case**
Insertion sort performs two operations:
1. scans through the list, comparing each pair of elements
2. performs a swap if these two elements are out of order

For the best case scenario (the array is already sorted), insertion sort would have a complexity of $\mathcal{O}(n)$, comparing all items but performing no swaps.

**Worst and Average Case**
The worst case would occur when the input list is in decreasing order. To insert the last element, we need at most $n - 1$ comparisons and at most $n - 1$ swaps. For the second to last element, $n - 2$ for both.

- The number of operations to perform the sort is therefore: $2 \times (1 + 2 + ... + (n-2) + (n-1)$
- To calculate the #recurrence-relation for this algorithm, use the following summation:
$$\sum_{q=1}^p q = \frac{p(p + 1)}{2}$$

It follows that;
$$\frac{2(n - 1)(n - 1 + 1)}{2} = n(n - 1)$$

- Using the #master-theorem this can be solved as $\mathcal{O}(n^2)$

- ==Insertion sort is stable with a space complexity of $\mathcal{O}(1)$==