# Binary Search
#learning #algorithms #binarysearch

## Algorithm
- Begin with the mid element of the whole array as a search key.
- If the value of the search key is equal to the item then return an index of the search key.
- Or if the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half.
- Otherwise, narrow it to the upper half.
- Repeatedly check from the second point until the value is found or the interval is empty.

## Implementation
### Iterative Method
```pseudocode
binarySearch(arr, x, low, high)
	repeat till low = high
	    mid = (low + high)/2
	    if (x == arr[mid])
	        return mid
   
        else if (x > arr[mid]) // x is on the right side
            low = mid + 1
   
        else                  // x is on the left side
            high = mid - 1
```

### Recursive Method
```pseudocode
binarySearch(arr, x, low, high)
    if low > high
        return False 
   
    else
        mid = (low + high) / 2 
        if x == arr[mid]
            return mid
       
    else if x > arr[mid]        // x is on the right side
        return binarySearch(arr, x, mid + 1, high)
               
    else                        // x is on the left side
        return binarySearch(arr, x, low, mid - 1)
```