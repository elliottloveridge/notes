## Binary Search Trees

**Binary search trees** (also known as binary trees or BSTs) contain sorted data arranged in a tree-like structure. 

- A binary tree consists of "root" and "leaf" data points, or nodes, that branch out in two directions.
- Binary trees store 'items' (numbers, names, etc.) in memory, ==allowing for fast lookup, addition, and removal of items==.
- They can be used to implement either dynamic dynamic sets of items or lookup tables that allow for finding an item by a key (key-value pair).

**Overview**
Each tree starts with a single root node that contains data as well as references to the left and right nodes. This pattern continues recursively.

### Operations

**Tree Traversal**
There are two primary ways to iterate through a tree;
1. Depth-first
	- The left subtree is search first, then the right subtree
2. Breadth-first
	- Processes through the nodes at each height level of the tree
	- Root node first, then level 1 nodes, then level 2 nodes, and so on.

**Tree Insertion**
To insert a node, find the leftmost leaf node that is less than the value being inserted, adding a child node to that node containing the inserted value.

**Deletion**
Deletion is less straightforward, there are three cases to consider:
1. If the deleted node has no children, remove the node from its parent
2. If the deleted node has one child, replace the node with its child
3. If the deleted node has two children;
	- Start with the current node's right child
	- Find that child's leftmost child
	- Replace the current node's value with the leftmost child's value
	- Call the deletion function on the current node's right child

### Tree Shape and Balancing
Inserting and deleting nodes in a binary tree affects the shape of the tree which can affect the efficiency of operations on the tree.

A balanced tree has the smallest possible height (node depth) and is the most efficient configuration for the tree for the set of all possible searches. ==Balancing must be performed regularly==.