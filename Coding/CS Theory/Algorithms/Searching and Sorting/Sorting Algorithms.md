# Sorting Algorithms

A **sorting algorithm** is an algorithm made up of a series of instructions that takes an [[Arrays|array]] (sometimes called a list) as an input, performs specified operations on the array and outputs a #permutation of that array that is sorted.

- Sorting may seem like a simple concept, but efficient sorting is critical when dealing with large amounts of data. 
- Sorting is the basis for more complex computer programs such as searching for files, compressing data, and finding the shortest route to a destination.

There are two broad types of sorting algorithms:
1. [[Integer Sort]]
2. [[Comparison Sort]]
	1. [[Merge Sort]] - focuses on how to merge together two pre-sorted [[Arrays|arrays]] such that the resulting array is also sorted
	2. [[Insertion Sort]] - builds a final sorted array one element at a time
	3. [[Bubble Sort]] - compares each pair of elements in an array and swaps them if they are out of order until the entire array is sorted
	4. [[Quick Sort]] - algorithm picks a pivot element, $A[q]$, and then rearranges the array into two sub-arrays split by the value of $A[q]$

### Properties
**Complexity**
- ==When working with each algorithm it is important to know how fast it runs and in how much space it operates (**time and space complexity**)==
- [[Comparison Sort|Comparison algorithms]] have a worst-case time complexity of $\mathcal{O}(n\log{n})$
- The time complexity describes how many operations an algorithm must carry out before it completes
- The space complexity describes how much space must be allocated to run a particular algorithm
	- If you take a list of size $n$, and for some reason make a new list of size $n$ for each element in $n$ then the algorithm needs $n^2$ space

**Stability**
It can be useful to know if a sorting algorithm is stable. 

- A sorting algorithm is stable if it preserves the original order of elements with equal key values
	- In the below example, the order of the (equal) 5's is kept if stable

![[sorting-stability.png|200]]