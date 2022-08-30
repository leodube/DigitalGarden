# 4. Median of Two Sorted Arrays
## Question
Given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively, return **the median** of the two sorted arrays.

The overall run time complexity should be `O(log (m+n))`.

###### Example 1:
```
Input: nums1 = [1,3], nums2 = [2]
Output: 2.00000
Explanation: merged array = [1,2,3] and median is 2.
```

###### Example 2:
```
Input: nums1 = [1,2], nums2 = [3,4]
Output: 2.50000
Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.
```

###### Constraints:
-   `nums1.length == m`
-   `nums2.length == n`
-   `0 <= m <= 1000`
-   `0 <= n <= 1000`
-   `1 <= m + n <= 2000`
-   `-106 <= nums1[i], nums2[i] <= 106`

---

## Solution
### Initial Solution
- We need to merge the arrays first, then find the median. 

###### Implementation
```typescript
function findMedianSortedArrays(nums1: number[], nums2: number[]): number {
    let i = 0;
    let j = 0;
    let len = nums1.length + nums2.length;
    let mNums = [];

	// loop through arrays
    while(nums1[i] != null && nums2[j] != null) {
        if (nums1[i] > nums2[j]) {
            mNums.push(nums2[j]);
            j++;
        } else if (nums1[i] < nums2[j]) {
            mNums.push(nums1[i]);
            i++;    
        } else {
            mNums.push(nums1[i]);
            mNums.push(nums2[j]);
            i++;
            j++;    
        }
    }

	// append any remaining parts of array
    if (nums1[i] != null)
        mNums.push(...nums1.slice(i));
    if (nums2[j] != null)
        mNums.push(...nums2.slice(j));    

	// calculate median
    if (len % 2) {
        return mNums[(Math.ceil(len/2)) - 1];
    } else {
        return (mNums[len/2] + mNums[(len/2)-1]) / 2;
    }
};
```

###### Analysis
- Runtime: 182 ms, faster than 49.81% of TypeScript online submissions for Median of Two Sorted Arrays.
- Memory Usage: 48.2 MB, less than 67.01% of TypeScript online submissions for Median of Two Sorted Arrays.

### No LeetCode solution