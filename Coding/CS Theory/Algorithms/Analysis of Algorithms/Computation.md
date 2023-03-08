# Intro to Computation
```Brilliant.org Course - Algorithms (2019)```

A function $f(x)$ takes an input and returns an output. A common example of a function in computer science is;
```python
sort(list)
```
which returns the original list in ascending order.

**Question - Combinations**
For `sort(list) = [1, 2, 3, 4]`, how many unique combinations can be made from these four digits?

==*There are $4! = 24$ different way of sorting these values within a list*==

---
- In math you don't offer consider the difficulty of computing a function but this is a central question within computer science.
- Computers know how to directly evaluate some "native" functions (like comparisons, addition, multiplication, etc.), and can only compute higher-order functions using these native operations.
- A central question is therefore how many native operations it takes to complete a higher-order function for different inputs.

**Example - List Sort**
Let's take a list object that has two native functions:

1.  You can compare any two values in the list to see which one is bigger.
2.  You can swap any two values in the list.

```python
lst = ['c', 'b', 'd', 'a']

n = len(lst)
assert n==4 

for i in range(n-1):
    for j in range(i+1,n):
        if lst[i] > lst[j]:
            lst.switch(i, j)

print('Sorted list: ' + str(lst))
```

- What are the maximum number of comparisons and switches?

For **comparisons**;

- for any size-four input there will always be 6 comparisons made.
	- because the number of comparisons made by our code isn't affected by the if-statement, and at every index `i` we make a comparison with every following index. For a four element list, this gives a total of $3 + 2 + 1 + 0 = 63$ comparisons.
	- ==At each index one element has been sorted and so the number of comparisons reduce each time==

For **switches**;

- There can only even be one switch per comparison, so the maximum number of switches would be 6.
	- This can be obtained if the element list was given in reverse order.

### General Theory
Above described the worst case for comparisons and switches but a more general theory can be applied