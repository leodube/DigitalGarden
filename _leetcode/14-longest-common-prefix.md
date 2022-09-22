# 14. Longest Common Prefix
## Question
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string `""`.

###### Example 1:
```
Input: strs = ["flower","flow","flight"]
Output: "fl"
```

###### Example 2:
```
Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

###### Constraints:
-   `1 <= strs.length <= 200`
-   `0 <= strs[i].length <= 200`
-   `strs[i]` consists of only lowercase English letters.
---
## Solution
### Initial Solution

```typescript
function longestCommonPrefix(strs: string[]): string {
    let pre = strs[0];
    
    for (let i=1; i<strs.length; i++) {
        for (let j=0; j<strs[i].length; j++) {
            pre = pre[j] != strs[i][j] ? pre.substring(0, j) : pre;
        }
        pre = pre.length > strs[i].length ? pre.substring(0, strs[i].length) : pre
    }
    
    return pre;
};
```

###### Analysis
- Runtime: 120 ms, faster than 31.78% of TypeScript online submissions for Longest Common Prefix.
- Memory Usage: 44 MB, less than 85.78% of TypeScript online submissions for Longest Common Prefix.

### LeetCode Solution 3: Divide and conquer
###### Intuition
The idea of the algorithm comes from the associative property of LCP operation. We notice that : $LCP(S_1 \ldots S_n) = LCP(LCP(S_1 \ldots S_k), LCP (S_{k+1} \ldots S_n))$, where $LCP(S_1 \ldots S_n)$ is the longest common prefix in set of strings $[S_1 \ldots S_n][S1​…Sn​] , 1 < k < n1<k<n$

###### Algorithm
To apply the observation above, we use divide and conquer technique, where we split the $LCP(S_i \ldots S_j)$ problem into two subproblems $LCP(S_i \ldots S_{mid})$ and $LCP(S_{mid+1} \ldots S_j)$, where `mid` is $\frac{i + j}{2}$. We use their solutions `lcpLeft` and `lcpRight` to construct the solution of the main problem $LCP(S_i \ldots S_j)$. To accomplish this we compare one by one the characters of `lcpLeft` and `lcpRight` till there is no character match. The found common prefix of `lcpLeft` and `lcpRight` is the solution of the $LCP(S_i \ldots S_j)$.

```typescript
function longestCommonPrefix(strs: string[]): string {
    if (strs == null || strs.length ==0) return "";
    return longestCommonPrefixRec(strs, 0, strs.length-1);
};

function longestCommonPrefixRec(strs: string[], l: number, r: number): string {
    if (l==r) return strs[l];
    let mid = Math.floor((l+r)/2);
    let lcpLeft = longestCommonPrefixRec(strs, l, mid);
    let lcpRight = longestCommonPrefixRec(strs, mid+1, r);
    return commonPrefix(lcpLeft, lcpRight);
}

function commonPrefix(left: string, right: string): string {
    let min = Math.min(left.length, right.length);
    for (let i=0; i<min; i++) {
        if (left[i] != right[i]) return left.substring(0, i);
    }
    return left.substring(0, min);
}
```