# Recursion

- Recursion is the process in which a function calls itself directly or indirectly (the corresponding function is called as recursive function)
- Recursive solutions help to solve certain problems

## Mathematical Interpretation
- Say you wanted to determine the sum of the first *n* natural numbers.
- The simplest approach would be to add the numbers starting from 1 to n
	- This would look like the following:
$$f(n) = 1 + 2 + 3 + \text{ ... } + n$$

- There is another mathematical way of representing this, the recursive way where $f(n) = 1 \text{ and } n = 1$ and:

$$f(n) = n + f(n-1) \text{ for } n > 1$$
### How It Works
- Recursion involves breaking a problem down into smaller sub-problems in order to obtain a solution. In general, every recursive solution consists of defining two parts;
	1. The base case: what should the algorithm do in the simplest solution?
	2. The inductive step: how does the algorithm build up the solution?

- [[Fibonacci Numbers]] is a good example of solving recursively
- The **downside** of recursion is that it can be very inefficient, [[Dynamic Programming|dynamic programming]] is a solution for this
