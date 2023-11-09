# Master Method

- Used to understand the time complexity of a recursive algorithm
- More specifically, the master method is a method to solve a recurrence

- $n$: the length of the input array
- $T(n)$: running time
- $a$: the number of children each node (subproblem) has
	- [[Binary Search|Binary search]] splits the original array into two parts each time so *a* is 2
- $T \left( \frac{n}{b} \right)$: the runtime of the initial nodes
- $f(n)$: asymptotically positive function

## Standard Form
- The master theorem provides a solution to recurrence relations of the form;
$$T(n) = aT \left( \frac{n}{b} \right) + f(n)$$
- A recursive tree has a depth of $\log_b{n}$ and depth $i$ contains $a^i$ nodes
	- So there are $a^{\log_b{n}} = n^{\log_b{a}}$ leaves
	- Hence, the runtime is $\Theta(n^{\log_b{a}})$

- There are three solutions for the standard form of the master method
	1. $O(n^d\log{n}) \text{ if } a = b^d$
	2. $O(n^d) \text{ if } a \lt b^d$
	3. $O(n^{\log_b{a}}) \text{ if } a \gt b^d$
