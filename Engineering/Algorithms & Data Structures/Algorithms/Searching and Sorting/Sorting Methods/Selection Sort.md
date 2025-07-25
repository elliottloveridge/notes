# Selection Sort

- Selection sort is a basic comparison based algorithm
- It has a time complexity of $O(n^2)$ in all cases
	- One positive is it does less memory writes vs other algorithms
- Unstable algorithm in its basic form
- In-place algorithm
	- Does not require extra memory for sorting

```python
def selection_sort(l):
    n = len(l)
    for i in range(n):
        min_ind = i
        for j in range(i + 1, n):
            if l[j] < l[min_ind]:
                min_ind = j
        l[min_ind], l[i] = l[i], l[min_ind]

    return l
```
