# Big-O Notation

## Computing Runtime
- Computing runtime requires a large amount of information
	- e.g. hardware (how fast is the computer you are using)
		- For a general rule, we assume their effect to change linearly for a differing input size
- We want to define a rule-of-thumb method to generalise runtime

### Asymptotic Notation
- Defines how runtime scales with input size
- Common runtime definitions: $\log{n} < \sqrt{n} < n < n\log{n} < n^2 < 2^n$

## Big-O Notation
- Clarifies growth rate
	- How runtime scales with input size
- **Definition**
	- Consider two functions $f(n)$ and $g(n)$ that are defined for all positive integers and take on non-negative real values
	- We say that $f(n)$ **grows slower than** $g(n)$ and write $f \prec g$ if;
		- $\frac{f(n)}{g(n)}$ goes to 0 as $n$ grows
	- We say that $f(n)$ **grows no faster than** $g(n)$ and write $f \preceq g$, if;
		- There exists a constant $c$ such that $f(n) \le c \cdot g(n)$ for all $n$
- Three important rules of this definition
	- $f \prec g$ is the same as $f=o(g)$ (small-o) and $f \preceq g$ is the same as $f=O(g)$ (big-O)
		- Do not think of $=$ in the normal sense for the above
			- In Big-O notation you could say $5n^2 = O(n^3)$ as well as $5n^2 = O(n^2)$
				- $5n^2$ grows no faster than both terms
	- If $f \prec g$, then $f \preceq g$
		- If $f$ grows slower than $g$, then $f$ certainly grows no faster than $g$
- It uses a $\preceq$ symbol instead of the standard $\le$ since the latter one is typically used as follows
	- $f \le g$ if $f(n) \le g(n)$ for all $n$. Hence, for example, $5n^2 \not \le n^2$, but $5n^2 \preceq n^2$

### Using Big-O
- Multiplicative constants can be ignored
- Smaller terms can be ignored

#### Fibonacci Example
1. Create a list of size n: $O(n)$
	- For every cell you have to set this equal to zero
2. Set `list[0] = 0`: $O(1)$
3. Set `list[1] = 0`: $O(1)$
4. Loop for `range(2, n)`: $O(n)$
	- `list[i] = list[i - 1] + list[i - 2]`: $O(n)$
5. Return `list`: $O(1)$

- Total: $O(n) + O(1) + O(1) + (O(n) \times O(n)) + O(1) = O(n^2)$

### Examples
- $\log_2{n} = O(n^2)$
	- A logarithmic function grows slower than a polynomial
- $5^{\log_2{n}} \neq O(n^2)$
	- $a^{\log_b{c}} = c^{\log_b{a}}$
	- $\therefore 5^{\log_2{n}} = n^{\log_2{5}} \approx n^{2.5}$
	- $n^{2.5}$ **does not** grow no faster than $n^2$
- $n\log_2{n} \neq O(n)$
	- To compare these, first cancel the $n$
		- Then, $\log_2{n} \neq 1$
- $n^2 = O(n^3)$
- $n \neq O(\sqrt{n})$
	- $\sqrt{n} = n^{0.5}$ grows slower than $n = n^1$
- $2^{3\log_2{n}} = O(n^5)$
	- $2^{3\log_2{n}} = (2^{\log_2{n}})^3 = n^3$
- $2^n = O(2^{n + 1})$
	- $2^{n + 1} = 2 \times 2^n$