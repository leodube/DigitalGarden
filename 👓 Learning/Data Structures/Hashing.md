# Hashing
#learning #datastructure #hashing #todo

## What is it?
Hashing is a technique or process of mapping keys, and values into the hash table by using a hash function. It is done for faster access to elements. The efficiency of mapping depends on the efficiency of the hash function used.

## Why is it used?
For **[[👓 Learning/Data Structures/Array|arrays]] and [[👓 Learning/Data Structures/Linked List|linked lists]]**, we need to search in a linear fashion, which can be costly in practice. If we use arrays and keep the data sorted, then a number can be searched in `O(Logn)` time using Binary Search, but insert and delete operations become costly as we have to maintain sorted order. 

In hashing, all the above operations (search, insert, delete) can be performed in O(1) i.e. constant time. It is important to understand that the worst case time complexity for hashing remains O(n) but the average case time complexity is O(1).

## Complexity
- **Insert:** $O(1)$
- **Search:** $O(1)$
- **Delete:** $O(1)$

## Implementation
### Insert
### Search
### Delete
