# 1. Two Sum
#lc/easy #lc/success

## Question
Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

###### Example 1:
```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

###### Example 2:
```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

###### Example 3:
```
Input: nums = [3,3], target = 6
Output: [0,1]
```

##### Constraints:
-   `2 <= nums.length <= 10^4`
-   `-10^9 <= nums[i] <= 10^9`
-   `-10^9 <= target <= 10^9`
-   **Only one valid answer exists.**

###### Follow-up:
Can you come up with an algorithm that is less than $O(n^2)$ time complexity?

---
## Solution
### Initial Solution
- The solution must have the form `[i,j]`, where `i` is the first index and `j` is the second index.
- The simplest approach is to try different pairs of numbers and see if they add up to the target.
- We can set `i` to 0 and `j` to the lenght of the list, then iterate `j` backwards until it reaches `i+1`. If we don't find any of the numbers add to the target, increase `i` by 1 and repeat.

```typescript
function twoSum(nums: number[], target: number): number[] {
    for (let i=0; i<nums.length; i++) {
        for (let j=nums.length-1; j>=0; j--) {
            if (i == j)
                continue;
            else if (nums[i] + nums[j] == target)
                return [i,j]
        }
    }
};
```

###### Analysis
>[!Success]
>- Runtime: 275 ms, faster than 13.85% of TypeScript online submissions for Longest Substring Without Repeating Characters.
>- Memory Usage: 43.3 MB, less than 99.27% of TypeScript online submissions for Longest Substring Without Repeating Characters.

>[!Note]
> There should be an algorithm that is less than $O(n^2)$ time complexity.
> - Time complexity: $O(n^2)$. For each element, we try to find its complement by looping through the rest of the array which takes $O(n)$ time. Therefore, the time complexity is $O(n^2)$.
> - Space complexity: $O(1)$. The space required does not depend on the size of the input array, so only constant space is used.

### LeetCode Solution 1: Two-Pass Hash Table
###### Intuition
To improve our runtime complexity, we need a more efficient way to check if the complement exists in the array. If the complement exists, we need to get its index. What is the best way to maintain a mapping of each element in the array to its index? A [[hashing|hash table]].

We can reduce the lookup time from $O(n)$ to $O(1)$ by trading space for speed. A hash table is well suited for this purpose because it supports fast lookup in _near_ constant time. I say "near" because if a collision occurred, a lookup could degenerate to $O(n)$ time. However, lookup in a hash table should be amortized $O(1)$ time as long as the hash function was chosen carefully.

###### Algorithm
A simple implementation uses two iterations. In the first iteration, we add each element's value as a key and its index as a value to the hash table. Then, in the second iteration, we check if each element's complement (`target - nums[i]`) exists in the hash table. If it does exist, we return current element's index and its complement's index. Beware that the complement must not be `nums[i]` itself!

###### Implementation
```typescript
function twoSum(nums: number[], target: number): number[] {
    let hashmap = {};
    for (let i=0; i<nums.length; i++) {
        hashmap[nums[i]] = i;
    }
    for (let i=0; i<nums.length; i++) {
        let complement = target - nums[i];
        if ((complement in hashmap) && hashmap[complement] != i) {
            return [i, hashmap[complement]];
        }
    }
};
```

### LeetCode Solution 2: One-Pass Hash Table
###### Algorithm
It turns out we can do it in one-pass. While we are iterating and inserting elements into the hash table, we also look back to check if current element's complement already exists in the hash table. If it exists, we have found a solution and return the indices immediately.

###### Implementation
```typescript
function twoSum(nums: number[], target: number): number[] {
    let hashmap = {};
    for (let i=0; i<nums.length; i++) {
        let complement = target - nums[i];
        if ((complement in hashmap) && hashmap[complement] != i) {
            return [i, hashmap[complement]];
        }
        hashmap[nums[i]] = i;
    }
};
```