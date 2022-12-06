# Binary Search Tree
#data-structure 

Also see [[binary-tree|Binary Tree]].

## What is it?
**Binary Search Tree** is a node-based binary tree data structure which has the following properties:

- The left subtree of a node contains only nodes with keys lesser than the node’s key.
- The right subtree of a node contains only nodes with keys greater than the node’s key.
- The left and right subtree each must also be a binary search tree.

![200px-Binary_search_tree.svg](https://media.geeksforgeeks.org/wp-content/uploads/BSTSearch.png "Click to enlarge")

The above properties of Binary Search Tree provides an ordering among keys so that the operations like search, minimum and maximum can be done fast. If there is no ordering, then we may have to compare every key to search for a given key.

## Why is it used?
### Advantages of BST over Hash Table
[[hashing|Hash Table]] supports following operations in $O(1)$ time: `Search`, `Insert`, `Delete`. The time complexity of above operations in a self-balancing Binary Search Tree is $O(Logn)$.  So Hash Table seems to beating BST in all common operations. When should we prefer BST over Hash Tables, what are advantages. Following are some important points in favor of BSTs.

1. We can get all keys in sorted order by just doing Inorder Traversal of BST. This is not a natural operation in Hash Tables and requires extra efforts.
2. Doing [order statistics](https://www.geeksforgeeks.org/find-k-th-smallest-element-in-bst-order-statistics-in-bst/), [finding closest lower and greater elements](https://www.geeksforgeeks.org/floor-and-ceil-from-a-bst/), [doing range queries](https://www.geeksforgeeks.org/print-bst-keys-in-the-given-range/) are easy to do with BSTs. Like sorting, these operations are not a natural operation with Hash Tables.
3. BSTs are easy to implement compared to hashing, we can easily implement our own customized BST. To implement Hashing, we generally rely on libraries provided by programming languages.
4. With Self-Balancing BSTs, all operations are guaranteed to work in $O(Logn)$ time. But with Hashing, $O(1)$ is average time and some particular operations may be costly i.e, $O(n^2)$, especially when table resizing happens.
5. In BST we can do range searches efficiently but in Hash Table we cannot do range search efficienly.
6. BST are memory efficient but Hash table is not.

## Complexity
- **Insert:** Worst case $O(h)$, where $h$ is height of tree (which can approach $n$)
- **Search:** Worst case $O(h)$, where $h$ is height of tree (which can approach $n$)
- **Delete:** Worst case $O(h)$, where $h$ is height of tree (which can approach $n$)

## Implementation
### Insert
1.   Start from the root. 
2.  Compare the inserting element with root, if less than root, then recursively call left subtree, else recursively call right subtree. 
3.  After reaching the end, just insert that node at left(if less than current) or else right.

```javascript
class Node {
	constructor(item) {
		this.key = item;
		this.left = this.right = null;
	}
}

// Root of BST
var root = null;

// Calls recursive insert
function insert(key) {
	root = insertRec(root, key);
}

// Recursive function to insert new key in BST
function insertRec(root, key) {
	// Base Case: If tree is empty, return a new node
	if (root == null) {
		root = new Node(key);
		return root;
	} 

	// Otherwise, recur down the tree
	if (key < root.key)
		root.left = insertRec(root.left, key);
	else if (key > root.key)
		root.right = insertRec(root.right, key);

	return root;
}
```

### Search
1.  Start from the root. 
2.  Compare the searching element with root, if less than root, then recursively call left subtree, else recursively call right subtree. 
3.  If the element to search is found anywhere, return true, else return false.

```javascript
function search (root, key) {
	// base case: root is null or is key
	if (root == null || root.key == key)
		return root;

	// key is greater than root's key
	if (root.key < key)
		return search(root.right, key);

	// key is less than root's key
	return search(root.left, key);
}
```

### Delete
**1)** _**Node to be deleted is the**_ _**leaf:**_ Simply remove from the tree.
**2)** _**Node to be deleted has only one child:**_ Copy the child to the node and delete the child
**3)** _**Node to be deleted has two children:**_ Find inorder successor of the node. Copy contents of the inorder successor to the node and delete the inorder successor. Note that inorder predecessor can also be used.

```javascript
// Root of BST
var root = null;

// Calls recursive delete
function delete(key) {
	root = deleteRec(root, key);
}

// Recursive function to delete a key in BST
function deleteRec(root, key) {
	// Base Case: if the tree is empty
	if (root == null)
		return root;

	// Otherwise recur down the tree
	if (key < root.key)
		root.left = deleteRec(root.left, key);
	else if (key > root.key)
		root.right = deleteRec(root.right, key);

	// If key is same as root's key, delete node
	else {
		// node with one or no child
		if (root.left == null)
			return root.right;
		else if (root.right == null)
			return root.left;

		// node with two children: get inorder successor
		root.key = minValue(root.right);

		// delete inorder successor
		root.right = deleteRec(root.right, root.key);
	}
	
	return root;
}

function minValue(root) {
	let minv = root.key;
	while (root.left != null) {
		minv = root.left.key;
		root = root.left;
	}
	return minv;
}
```
