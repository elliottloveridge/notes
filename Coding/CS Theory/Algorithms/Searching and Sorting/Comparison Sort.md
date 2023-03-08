## Comparison Sorts

Comparison sorts compare elements at each step of the algorithm to determine if one element should be to the 'left' or 'right' of another.

They are usually more straightforward to implement than [[Integer Sort|interger sorts]], but are limited by a #lower-bound-complexity of $\mathcal{O}(n\log{n})$ (on average they cannot be faster than this).
- ==The 'on average' here is because some sorts may be quicker due to them being partially sorted==

### Proof - Running time of comparison-based sorting is bounded by $\Omega(n\log{n})$

A comparison sort can be modeled as a large [[Binary Search Trees|binary tree]] called a *decision tree* where each node represents a single comparison.

- For a list of length $n$ there are $n!$ possible permutations
	- Each of these permutations is represented by a path through the decision tree (a series of comparisons and outcomes)
	- At each level of the tree a comparison is made
	- Each comparison halves the number of future comparisons the algorithm must do (as you have chosen either a left or right path)
		- ==The algorithm therefore performs $\mathcal{O}(\log{n!})$ comparisons==


- A binary tree of height $h$ has a number of leaves less than or equal to $2^h$

$$2^h \geq n!$$

- Taking the logarithm (base 2) gives;

$$h \geq \log(n!)$$

- From [[Stirling Approximation|Stirling's approximation]];

$$n! \gt (\frac{n}{e})^n$$

Therefore;

$$h \geq \log{(\frac{n}{e})^n}$$

$$= \log{(\frac{n}{e})}$$

$$= n\log{n} - n\log{e}$$

$$= \Omega(n\log{n})$$

---

### Types of Comparison Sort
1. [[Merge Sort]]
2. [[Insertion Sort]]
3. [[Bubble Sort]]