# Linked List
#data-structure #todo/ds 

## What is it?
Like arrays, Linked List is a linear data structure. Unlike arrays, linked list elements are not stored at a contiguous location; the elements are linked using pointers. They include a series of connected nodes. Here, each node stores the data and the address of the next node.
  
![](https://media.geeksforgeeks.org/wp-content/uploads/20220816144425/LLdrawio.png)

###### Types of Linked Lists:
-   **Simple Linked List** – In this type of linked list, one can move or traverse the linked list in only one direction
-   **Doubly Linked List** – In this type of linked list, one can move or traverse the linked list in both directions (Forward and Backward)
-   **Circular Linked List** – In this type of linked list, the last node of the linked list contains the link of the first/head node of the linked list in its next pointer and the first/head node contains the link of the last node of the linked list in its prev pointer

## Why is it used?
Arrays can be used to store linear data of similar types, but arrays have the following limitations:
- **The size of the arrays is fixed:** So we must know the upper limit on the number of elements in advance.
- **Insertion of a new element / Deletion of a existing element in an array of elements is expensive:**  The room has to be created for the new elements and to create room existing elements have to be shifted but in Linked list if we have the head node then we can traverse to any node through it and insert new node at the required position.

###### Advantages of Linked Lists over arrays:
-   Dynamic Array.
-   Ease of Insertion/Deletion.

## Complexity
- **Insert:** $O(1)$
- **Search:** $O(n)$
- **Delete:** $O(1)$

## Implementation
```javascript
class Node {
	constructor(val) {
		this.data = val;
		this.next = null;
	}
}

// create linked list with 3 nodes
var head = new Node(1);
var second = new Node(2);
var third = new Node(3);

head.next = second;
second.next = third;
```

##### Traversal of a Linked List
```javascript
var n = head;
while (n != null) {
	// do something
	n = n.next;
}
```


### Insert
### Search
### Delete