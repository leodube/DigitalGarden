# 26. Remove Duplicates From Sorted Array
#lc/easy #lc/success 

## Question
Given an integer array `nums` sorted in **non-decreasing order**, remove the duplicates in-place such that each unique element appears only **once**. The **relative order** of the elements should be kept the **same**.

Since it is impossible to change the length of the array in some languages, you must instead have the result be placed in the **first part** of the array `nums`. More formally, if there are `k` elements after removing the duplicates, then the first `k` elements of `nums` should hold the final result. It does not matter what you leave beyond the first `k` elements.

Return `k` _after placing the final result in the first_ `k` _slots of_ `nums`.

Do **not** allocate extra space for another array. You must do this by **modifying the input array in-place** with O(1) extra memory.

**Custom Judge:**

The judge will test your solution with the following code:
```
int[] nums = [...]; // Input array
int[] expectedNums = [...]; // The expected answer with correct length

int k = removeDuplicates(nums); // Calls your implementation

assert k == expectedNums.length;
for (int i = 0; i < k; i++) {
    assert nums[i] == expectedNums[i];
}
```

If all assertions pass, then your solution will be **accepted**.

###### Example 1:**
```
Input: nums = [1,1,2]
Output: 2, nums = [1,2,_]
Explanation: Your function should return k = 2, with the first two elements of nums being 1 and 2 respectively.

It does not matter what you leave beyond the returned k (hence they are underscores).
```

###### Example 2:**
```
Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
Explanation: Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.

It does not matter what you leave beyond the returned k (hence they are underscores).
```

**Constraints:**
-   `1 <= nums.length <= 3 * 104`
-   `-100 <= nums[i] <= 100`
-   `nums` is sorted in **non-decreasing** order.
---
## Solution
### Initial Solution

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int count = 1;
        int max = nums[nums.length-1];
        int prev = nums[0];
        
        // loop through array
        for (int i=1; i<nums.length; i++) {
            // if we reach the max number, exit
            if (prev == max) break;
            
            // if we find a duplicate, or a smaller number
            if (nums[i] <= prev) {
                // find next number that is not duplicate and is larger
                for (int j=i; j<nums.length; j++) {
                    if (nums[j] > prev) {
                        // swap numbers
                        int temp = nums[j];
                        nums[i] = nums[j];
                        nums[j] = temp;
                                                
                        // don't need to continue
                        break;
                    }
                }
            }
            
            // update previous
            prev = nums[i];
            // update count
            count++;
        }
        
        return count;
    }
}

```

###### Analysis
>[!Success]
> - Runtime: 5 ms, faster than 12.13% of Java online submissions for Remove Duplicates from Sorted Array.
>- Memory Usage: 48.1 MB, less than 28.63% of Java online submissions for Remove Duplicates from Sorted Array.

### LeetCode Solution 1: Two indexes approach
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int insertIndex = 1;
        for(int i = 1; i < nums.length; i++){
            // We skip to next index if we see a duplicate element
            if(nums[i - 1] != nums[i]) {
                /* Storing the unique element at insertIndex index and incrementing
                   the insertIndex by 1 */
                nums[insertIndex] = nums[i];     
                insertIndex++;
            }
        }
        return insertIndex;
    }
}
```

This approach is way simpler than mine. 
- Same idea to start at `index=1`
- Compare current `num` to previous `num`, however we check if they are not equal.
- If they aren't, we insert it at the `insertIndex`.

![](https://leetcode.com/problems/remove-duplicates-from-sorted-array/Figures/26/representation.png)

