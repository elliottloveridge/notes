# Hash Functions
- A hash function gets rid of the limitations of the [Direct Address Tables](Direct%20Address%20Tables.md)
- Given any kind of key
		- Phone number, names, Employee ID, etc.
- Use the hash function to convert them into small values as an index in an array
	- Essentially converting it into the direct address table
- Hash functions convert large keys into smaller values
## Requirements
- A hash function needs to meet certain requirements
- It should:
	- Always map a large key to the **same** small key
	- Generate only values from $0 \rightarrow (m-1)$ where $m$ is the size of the hash table
	- Be fast
		- $\mathcal{O}(1)$ for int and $\mathcal{O}(\text{len})$ for string of length `len`
	- Uniformly distribute large keys into hash table slots
		- This is the toughest part to achieve
			- How do you ensure that 100 phone numbers go to different values
## Example Functions
### Integer Hash Function
- Modulus function (e.g. $\mod{(\text{number})}$)
	- Still possible for two keys to convert into the same hash key
		- This is handled with **collision handling**
	- The modulus, $m$, is chosen as a prime number close to your hash table size
		- You should avoid powers
		- $m = 2^3$ would just evaluate the final 3 digits of a phone number
### String Hash Function
- `str = "abcd"`
- Key: `str[0] * x^0 + str[1] * x^1 + ...`
	- Problem: all permutations of a string would go into the same hash key
		- `"dcba"`, `"bcda"`, etc.
	- Take $\mod{(m)}$ of this where $m$ is the table size to counter this issue

