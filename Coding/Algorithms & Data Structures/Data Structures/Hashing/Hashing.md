# Hashing
## Why Use Hashing
- Hashing is mainly used when implementing dictionaries (also sets)
	- For dictionaries you have key-value pairs (for sets you only have keys)
### Benefits
- It provides **search**, **insert**, and **delete** in $\mathcal{O}(1)$ time on average
	- If a key already exists, insertion overwrites the previous value
	- In hash tables (and hashing), keys are unique
		- Hashing is a strict search where the key is either present or not
- The delete operation deletes the key and its corresponding value
#### vs Other Data Structures
##### Array
- If you store the keys in a sorted array then on average it would take $\mathcal{O}(\log{n})$ for search
	- For unsorted it would be $\mathcal{O}(n)$ (you have to check every item in the array)
- It would be linear, $\mathcal{O}(n)$, for insertion and delete as you need to shift all values within the array
##### Binary Search Tree
- $\mathcal{O}(\log{n})$ for search, insert, and delete
- There is a benefit to this data structure
	- Certain binary search trees can find a key just smaller or above a given key in $\mathcal{O}(\log{n})$
	- If you had to find the closest value with hashing that would take $\mathcal{O}(n)$
		- Getting keys in a sorted order would also not be optimal with hashing
## Applications of Hashing
- The hash table is one of the most used data structures in CS
	- Hashing is the technique behind it
- Applications include:
	- Dictionaries
	- Database indexing
		- Use indexing to quickly find records
			- Primary and secondary indexing allowed
			- This can be implemented via B-trees or Hashing
	- Cryptography
		- When you login to a website and enter your password
			- The password is not stored in plain text form
				- Compare output of a hash function with a stored hash
	- Caches
		- Browser cache have local data associated with different URLs
			- Key = URL, associated data = value
	- Symbol tables in compilers/interpreters
		- Variables need to be looked up quickly to find out their memory addresses
	- Routers
		- Home router connected to a local network (and the internet)
			- For local devices, you need to find which device corresponds to a given IP address
	- Getting data from databases
		- Uses columns as keys
