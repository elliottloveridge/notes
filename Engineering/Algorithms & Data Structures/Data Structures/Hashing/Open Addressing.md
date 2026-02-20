# Open Addressing
- Another way to handle collisions
- Use a single array only (no chains or other data structures)
- Number of slots in the hash table needs to be greater than number of keys to be inserted
- Advantage over chaining
	- Cache friendly (will have fewer cache misses)
- There are multiple ways to handle open addressing
	- Linear probing
	- Quadratic probing
	- Double hashing
## Insert with Open Addressing
- For linear probing, when you have a key collision, you linearly search for the next available (empty) slot in the array
	- You search in a circular manner (if the final slot is empty, go back to the start of the array)
## Search with Open Addressing
- Find the hash function value
- If the slot is occupied with another value, search in the next available slots until you find the value
	- Also possible to find an empty slot (searching for something that doesn't exist or recently deleted)
	- If the entire table is filled with non-matching values then you would search until you return to the original key location and then say the value was not present
		- Search the entire hash table
## Delete with Open Addressing
- Problem: If you make a slot empty, other values that were linearly probed further than this would return value not found (even though it's in the hash table at a later index)
- Flag the slot as deleted (not empty) so that a search does not stop
	- Insert can still insert into a deleted slot
## Clustering
- A cluster is a group of keys within the hash table
	- Inserting after a collision increases the cluster of size $k$ by 1
- Clusters impact performance of operations
- Secondary clusters in quadratic probing
	- $\text{hash}(\text{key}, i) = (h(\text{key}) + i^2) \mod 7$
		- Goes to 4th, 9th, etc. slot instead of 1st, 2nd, etc.
		- Better than primary clustering
	- Has a disadvantage vs linear probing
		- Might not find an empty slot even if there are some