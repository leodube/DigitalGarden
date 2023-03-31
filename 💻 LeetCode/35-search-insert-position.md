# 35. Search Insert Position
#leetcode #easy #success

## Question
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with `O(log n)` runtime complexity.

###### Example 1:
```
Input: nums = [1,3,5,6], target = 5
Output: 2
```

###### Example 2:
```
Input: nums = [1,3,5,6], target = 2
Output: 1
```

###### Example 3:
```
Input: nums = [1,3,5,6], target = 7
Output: 4
```

###### Constraints:
-   `1 <= nums.length <= 104`
-   `-104 <= nums[i] <= 104`
-   `nums` contains **distinct** values sorted in **ascending** order.
-   `-104 <= target <= 104`
---
## Solution
### Initial Solution

```typescript
class Solution {
	public int searchInsert(int[] nums, int target) {
		// Intuition: use binary search
		int low = 0;
		int high = nums.length - 1;
		
		while(low <= high) {
			int mid = (low+high)/2;
			if (target == nums[mid]) return mid;
			else if (target > nums[mid]) low = mid + 1;
			else high = mid - 1;
		}
		return low;
	}
}
```

###### Analysis
>[!success]
> -   Runtime: 0 ms, faster than 100% of Java online submissions for Search Insert Position.
> -   Memory Usage: 43.8 MB, less than 24.14% of Java online submissions for Search Insert Position.

### LeetCode Solution
>[!Note]
>Premium required

### User Solution
Pretty much the same as above.