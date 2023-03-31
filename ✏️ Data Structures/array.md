# Array
#data-structures #array

## What is it?
An array is a collection of items stored at contiguous memory locations. The idea is to store multiple items of the same type together. This makes it easier to calculate the position of each element by simply adding an offset to a base value, i.e., the memory location of the first element of the array (generally denoted by the name of the array).

![Array Data Structure](https://media.geeksforgeeks.org/wp-content/uploads/array-2.png "Click to enlarge")

## Why is it used?
###### Advantages
-   Arrays allow random access to elements. This makes accessing elements by position faster.
-   Arrays have better [cache locality](https://en.wikipedia.org/wiki/Locality_of_reference) which makes a pretty big difference in performance.
-   Arrays represent multiple data items of the same type using a single name.

###### Disadvantages
You can’t change the size i.e. once you have declared the array you can’t change its size because of static memory allocation. Here insertion(s) and deletion(s) are difficult as the elements are stored in consecutive memory locations and the shifting operation is costly too.

###### Applications
-   Array stores data elements of the same data type.
-   Arrays are used when the size of the data set is known.
-   Used in solving matrix problems.
-   Applied as a lookup table in computer.
-   Databases records are also implemented by the array.
-   Helps in implementing sorting algorithm.
-   The different variables of the same type can be saved under one name.
-   Arrays can be used for CPU scheduling.
-   Used to Implement other data structures like [[✏️ Data Structures/Stack|Stacks]], [[✏️ Data Structures/Queue|Queues]], [[✏️ Data Structures/Heap|Heaps]], [[✏️ Data Structures/Hashing|Hash tables]], etc.

## Complexity
- **Insert:** $O(1)$ to insert a single element, $O(N)$ to insert all the array elements
- **Search:** $O(N)$
- **Access:**  $O(1)$ 

## Implementation
```javascript
let arr = [];
```

### Insert
```javascript
arr[0] = 1;
```

### Search
```javascript
for (let i=0; i<arr.length; i++) {
	if (arr[i] == value)
		return truel
}
```

### Access
```javascript
console.log(arr[0]);
```