# Collision Handling
- You have a big universe of values to hash and a small number of hash keys
	- It's therefore likely that two values will have the same hash key
- If you know all possible values that you need to hash in advance then you can use perfect hashing
	- No chance of shared hash keys if doing this (advanced hash method)
- If you do not know the keys in advance then collisions are almost guaranteed to happen
- There are two methods to handle collisions
-  Chaining
- Open Addressing
### Chaining
- Given the below input keys and a hash function of the form `hash(key) = key % 7`
	- `input = {50, 21, 58, 17, 15}`
- You also have a hash table
	- This is an array of linked list headers
		- There are other ways to implement a hash table
	- Why do we need linked lists?
		- If a collision happens then you add another node to the end of the linked list
#### Performance
- If `m` is the number of slots in the hash table and you have `n` keys to be inserted
- Load factor: $\alpha = \frac{n}{m}$
	- You can create a hash map/set in Java (or an unordered map/set in C++) using standard libraries
		- They provide you the option to specify the load factor
	- Load factor is a trade-off between speed and size
		- If the hash table is small (or load factor is large) then you will have more collisions
- Expected chain length: $\alpha$ (Load factor)
	- We don't know exactly the average case
		- Assume all keys are uniformly distributed in the hash table
- Expected time to search/insert/delete: $\mathcal{O}(1 + \alpha)$