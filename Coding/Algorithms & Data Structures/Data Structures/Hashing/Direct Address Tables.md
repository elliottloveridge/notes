## Direct Address Tables
- Direct address tables can be thought of as the end goal of a hash table
- In practice, they are an array based index lookup table
## Example
- Imagine a situation where you have 1000 keys with values from 0-999
	- How would you implement search, insertion, and delete in $\mathcal{O}(1)$ time?
		- You could create a boolean array of size 1000
			- All values are in the array are either 0 or 1 (key is not present or present)
		- You can get the value at a given index in $\mathcal{O}(1)$ time
	- This is dependent on your keys being within a set range
## Problems
- Cannot handle large values
	- An array for phone numbers (10 digits) would have a table of size 10^10 (number of possible unique 10 digit values)
- Cannot handle floating point numbers
- Cannot handle strings
- [Hash Functions](Hash%20Functions.md) and [Hash Tables](Hash%20Tables.md) are an answer to these issues