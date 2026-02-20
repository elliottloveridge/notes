## Dynamic Programming
### Fibonacci Numbers

`
Question: Write a function fib(n) that takes in a number as an argument. The function should return the nth number of the Fibonacci sequence.
`

fib(n): 1, 1, 2, 3, 5, 8, 13, ...

## Recursive Solution
```python
def fib(n):

    # base case - first two numbers in sequence are 1
    if n <= 2:
        return 1
    # recursive function call for previous two values
    return fib(n - 1) + fib(n - 2)
```

This function is **slow** to run.

### Problems
It is helpful to visualise this problem as a tree.

For the 7th Fibonacci number this would look like the tree below. From this tree you can see that there is a lot of duplicate computation (same subtree's within the full tree)

![[fibonacci-tree.png|400]]

#### Complexity of Recursive Solution
This solution has a time complexity of $\mathcal{O}(2^n)$ - exponential.

To explain this, first consider the following dummy function;

```python
def dib(n):

	if n <= 1:
		return 1
	dib(n - 1)
	dib(n - 1)
```

The tree for this function would be the following;
![[foo-tree.png|400]]

The left-most path is a linear structure {5, 4, 3, 2, 1} - showing that the tree has a height of $n$. 

Going down each level of the tree, the number of nodes is a function of $2^n$ meaning this structure has a time complexity of $\mathcal{O}(2^n)$ (the time to evaluate all of the function calls).

**Space Complexity**
Going down the left-most path again, you would add {5, ,4, 3, 2, 1} to the [[Stack|stack]]. 

However, when you reach the base case (leaf node) the function returns. When a function is returned its stack frame is removed or *popped* from the stack.

The most number of stack frames you use at one time is therefore 5 (or more generally, the height of the tree $n$).

---

Going back to the `dib(n)` function, if you instead reduced by $n - 2$ on each recursive function call, you would have a tree depth/height of $\frac{n}{2}$. 

- The time complexity of this new function could therefore be seen as $\mathcal{O}(2^\frac{n}{2})$
- However, in [[Big-O|O-notation]] you remove the less dominant terms so this can also be written as $\mathcal{O}(2^n)$.

==Going back to the Fibonacci function, this can be seen as sitting in the middle of the these two example functions, therefore also taking $\mathcal{O}(2^n)$ time.==
- The space complexity is also the same as defined above, $\mathcal{O}(n)$.

### Memoisation Solution
Using [[Memoisation|memoisation]], you are able to store values in a #hash-map of overlapping sub-problems (this is dynamic programming).

```python
# dict uses key:value pair of n:fib(n)
def fib(n, memo = dict()):

    # is the current arg (n) already calculated and stored
    if n in memo:
        return memo[n]
	# base case - first two values are 1
    elif n <= 2:
        return 1
    else:
		# store recursive function call value in dict
        memo[n] = fib(n - 1) + fib(n - 2)

    return memo[n]
```

#### Complexity of Memoisation Solution
It once again helps to look at a tree to understand the time and space complexity of the problem.

![[fib-memo-tree.png|200]]

Seen above, for each new value of $n$ you are adding to the tree in a linear way.
- Looking at the left nodes there are $n$ function calls, with one partner node.
- You therefore have $2n$ calls that can be simplified to $\mathcal{O}(n)$.
- The space complexity is also $\mathcal{O}(n)$.