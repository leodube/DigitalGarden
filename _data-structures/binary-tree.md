# Binary Tree
## What is it?
A **tree** is a popular data structure that is non-linear in nature. Unlike other data structures like array, stack, queue, and linked list which are linear in nature, a tree represents a hierarchical structure. The ordering information of a tree is not important. A tree contains nodes and 2 pointers. These two pointers are the left child and the right child of the parent node. Let us understand the terms of tree in detail.

- **Root:** The root of a tree is the topmost node of the tree that has no parent node. There is only one root node in every tree.
- **Edge:** Edge acts as a link between the parent node and the child node.
- **Leaf:** A node that has no child is known as the leaf node. It is the last node of the tree. There can be multiple leaf nodes in a tree.
- **Subtree:** The subtree of a node is the tree considering that particular node as the root node.
- **Depth:** The depth of the node is the distance from the root node to that particular node.
- **Height:** The height of the node is the distance from that node to the deepest node of that subtree.
- **Height of tree:** The Height of the tree is the maximum height of any node. This is same as the height of root node

![Binary Tree Data Structure](https://media.geeksforgeeks.org/wp-content/cdn-uploads/binary-tree-to-DLL.png "Click to enlarge")
###### Binary Tree Representation
A Binary tree is represented by a pointer to the topmost node of the tree. If the tree is empty, then the value of the root is NULL.

Binary Tree node contains the following parts:
1. Data
2. Pointer to left child
3. Pointer to right child

###### Basic Operation On Binary Tree:  
- Inserting an element.
- Removing an element.
- Searching for an element.
- Traversing an element.

###### Auxiliary Operation On Binary Tree:
- Finding the height of the tree
- Find the level of the tree
- Finding the size of the entire tree.

## Why is it used?
1. One reason to use trees might be because you want to store information that naturally forms a hierarchy. For example, the file system on a computer.
2. Trees (with some ordering e.g., BST) provide moderate access/search (quicker than Linked List and slower than arrays).   
3. Trees provide moderate insertion/deletion (quicker than Arrays and slower than Unordered Linked Lists).   
4. Like Linked Lists and unlike Arrays, Trees don’t have an upper limit on the number of nodes as nodes are linked using pointers.

## Complexity
- **Insert:** $O(n)$ where n is the number of nodes
- **Search:** $O(n)$ where n is the number of nodes
- **Delete:** #todo

## Implementation
```javascript
class Node
{
	constructor(item)
	{
		this.key = item;
		this.left = this.right = null;
	}
}
```

### Insert (Level Order)
The idea is to do an iterative level order traversal of the given tree using [[queue]]. If we find a node whose left child is empty, we make a new key as the left child of the node. Else if we find a node whose right child is empty, we make the new key as the right child. We keep traversing the tree until we find a node whose either left or right child is empty.

```javascript
let root;

function insert(root, key) {
	if (root == null) {
		root = new Node(key);
		return
	}
	
	let q = [];
	let tempNode;
	q.push(root);

	// do level order traversal
	while (q.length) {
		tempNode = q.shift();

		if (tempNode.left == null) {
			tempNode.left = new Node(key);
			break;
		} else {
			q.push(tempNode.left);
		}
		
		if (tempNode.right == null) {
			tempNode.right = new Node(key);
			break;
		} else {
			q.push(tempNode.right);
		}
	}
}
```

### Search
###### PreOrder Traversal
Here, the traversal is: root – left child – right child. It means that the root node is traversed first then its left child and finally the right child. Used to create a copy of the tree, or to get prefix expression on an expression tree.

```javascript
function preOrder(node) {
	if (node == null) return;
	// do something
	preOrder(node.left);
	preOrder(node.right);
}
```

###### InOrder Traversal
Here, the traversal is: left child – root – right child.  It means that the left child is traversed first then its root node and finally the right child.

```javascript
function inOrder(node) {
	if (node == null) return;
	inOrder(node.left);
	// do something
	inOrder(node.right);
}
```

###### PostOrder Traversal
Here, the traversal is: left child – right child – root.  It means that the left child is traversed first then the right child and finally its root node. Used to delete a tree.

```javascript
function inOrder(node) {
	if (node == null) return;
	preOrder(node.left);
	preOrder(node.right);
	// do something
}
```


### Delete
#todo
