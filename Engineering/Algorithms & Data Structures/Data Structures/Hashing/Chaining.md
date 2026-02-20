# Chaining
## Data Structures for Storing Chains
- Linked list (simple implementation)
	- Search: $\mathcal{O}(l)$, Delete: $\mathcal{O}(l)$, Insert: $\mathcal{O}(l)$ where $l$ is the chain length
- Dynamic sized array: $\mathcal{O}(l)$ for all operations
	- Vector in C++, arraylist in Java, list in Python
	- Dynamic sized arrays are cache friendly though (contiguous locations)
- Self balancing binary search tree (BST): $\mathcal{O}(\log{l})$
	- They are not cache friendly
## Implementing Chaining in Python
- Will be implemented as a list of lists
	- The inner list are the chains for each key
```python
class Hash:

	def __init__(self, b):
		self._bucket = b
		self.table = [[] for x in range(b)]

	def _hash(self, x):
		return x % self._bucket

	def insert(self, x):
		i = self._hash(x)
		self.table[i].append(x)

	def remove(self, x):
		i = self._hash(x)
		if x in self.table[i]:
			self.table[i].remove(x)

	def search(self, x):
		i = self._hash(x)
		return x in self.table[i]
```