# 3. Longest Substring Without Repeating Characters
#lc/medium #lc/success

## Question
Given a string `s`, find the length of the **longest substring** without repeating characters.

###### Example 1:
```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

###### Example 2:
```
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

###### Example 3:
```
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

###### Constraints
-   `0 <= s.length <= 5 * 104`
-   `s` consists of English letters, digits, symbols and spaces.

---
## Solution
### Initial Solution
- Ideally we want to loop through the string once.
- Start at first element, store in a [[hashing|hashmap]] (and maybe also a string). Go to next element and check if it is in the hashmap (we want a fast lookup time here). If not, add it to the hashmap and string. Continue until a repeat character is hit. Then move to second element and repeat.
- We might be able to furthur speed this up

```typescript
function lengthOfLongestSubstring(s: string): number {
    let curr = "";
    let longest = "";
    
    for (let i=0; i<s.length; i++) {
        let map = {};
        map[s[i]] = 1;
        curr += s[i];
        for (let j=i+1; j<s.length; j++) {
            if (s[j] in map) {
                break;
            } else {
                map[s[j]] = 1;
                curr += s[j];
            }
        }
        if (curr.length > longest.length)
            longest = curr;
        
        curr = "";
    }
    
    return longest.length
};
```

###### Analysis
> [!Success]
> 
> - Runtime: 609 ms, faster than 15.83% of TypeScript online submissions for Longest Substring Without Repeating Characters.
> - Memory Usage: 66.7 MB, less than 7.39% of TypeScript online submissions for Longest Substring Without Repeating Characters.

### LeetCode Solution 2: Sliding Window
###### Intuition
Given a substring with a fixed end index in the string, maintain a HashMap to record the frequency of each character in the current substring. If any character occurs more than once, drop the leftmost characters until there are no duplicate characters.

###### Algorithm
The naive approach is very straightforward. But it is too slow. So how can we optimize it?

In the naive approaches, we repeatedly check a substring to see if it has duplicate character. But it is unnecessary. If a substring $s_{ij}$ from index $i$ to $j - 1$ is already checked to have no duplicate characters. We only need to check if $s[j]$ is already in the substring $s_{ij}$.

To check if a character is already in the substring, we can scan the substring, which leads to an $O(n^2)$ algorithm. But we can do better.

By using HashSet as a sliding window, checking if a character in the current can be done in $O(1)$.

A sliding window is an abstract concept commonly used in array/string problems. A window is a range of elements in the array/string which usually defined by the start and end indices, i.e. $[i, j)$ (left-closed, right-open). A sliding window is a window "slides" its two boundaries to the certain direction. For example, if we slide $[i, j)$ to the right by 11 element, then it becomes $[i+1, j+1)$ (left-closed, right-open).

Back to our problem. We use HashSet to store the characters in current window $[i, j)$ ($j = i$ initially). Then we slide the index $j$ to the right. If it is not in the HashSet, we slide $j$ further. Doing so until $s[j]$ is already in the HashSet. At this point, we found the maximum size of substrings without duplicate characters start with index $i$. If we do this for all $i$, we get our answer.

###### Implementation
```typescript
function lengthOfLongestSubstring(s: string): number {
	let chars = {};
	let left = 0;
	let right = 0;
	let res = 0;

	while (right < s.length) {
		let r = s[right];
		chars[r] = (chars[r] ? chars[r] : 0) + 1;

		while (chars[r] > 1) {
			let l = s[left];
			chars[l] = chars[l] - 1;
			left++;
		}

		res = Math.max(res, right-left+1);
		right++;
	}

	return res;
}
```

###### Complexity Analysis
-   Time complexity : $O(2n) = O(n)$. In the worst case each character will be visited twice by i and j.
-   Space complexity : $O(min(m, n))$. Same as the previous approach. We need $O(k)$ space for the sliding window, where k is the size of the `Set`. The size of the Set is upper bounded by the size of the string nn and the size of the charset/alphabet m.

### LeetCode Solution 3: Sliding Window Optimized
###### Intuition
The above solution requires at most 2n steps. In fact, it could be optimized to require only n steps. Instead of using a set to tell if a character exists or not, we could define a mapping of the characters to its index. Then we can skip the characters immediately when we found a repeated character.

###### Algorithm
The reason is that if $s[j]$ have a duplicate in the range $[i, j)$ with index $j'$, we don't need to increase $i$ little by little. We can skip all the elements in the range $[i, j']$ and let $i$ to be $j' + 1$ directly.

###### Implementation
```typescript
function lengthOfLongestSubstring(s: string): number {
	let ans = 0;
	let map = {};
	for (let i=0, j=0; j<s.length; j++) {
		if (s[j] in map){
			i = Math.max(map[s[j]], i);
		}
		ans = Math.max(ans, j-i+1);
		map[s[j]] = j+1;
	}
	return ans;
}
```