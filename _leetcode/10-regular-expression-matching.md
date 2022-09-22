# #10. Regular Expression Matching
## Question
Given an input string `s` and a pattern `p`, implement regular expression matching with support for `'.'` and `'*'` where:

-   `'.'` Matches any single character.​​​​
-   `'*'` Matches zero or more of the preceding element.

The matching should cover the **entire** input string (not partial).

###### Example 1:
```
Input: s = "aa", p = "a"
Output: false
Explanation: "a" does not match the entire string "aa".
```

###### Example 2:
```
Input: s = "aa", p = "a*"
Output: true
Explanation: '*' means zero or more of the preceding element, 'a'. Therefore, by repeating 'a' once, it becomes "aa".
```

###### Example 3:
```
Input: s = "ab", p = ".*"
Output: true
Explanation: ".*" means "zero or more (*) of any character (.)".
```

###### Constraints:
-   `1 <= s.length <= 20`
-   `1 <= p.length <= 30`
-   `s` contains only lowercase English letters.
-   `p` contains only lowercase English letters, `'.'`, and `'*'`.
-   It is guaranteed for each appearance of the character `'*'`, there will be a previous valid character to match.


---
## Solution
- Read in pattern first.
- Go through input string character by character. 

```
function isMatch(s: string, p: string): boolean {
    let j = 0;
    let ast = false;
    let prev = ""
    for (let i=0; i<s.length; i++) {
        switch (p[j]) {
            case "*":
                ast = true;
                break;
            case ".":
                if (!ast) j++;
                break;
            default:
                if (p[j] != s[i] && s[i] != prev && p[j+1] != "*") return false;
                if (p[j+1] == "*"){
                    prev = p[j];
                }
                if (ast && (s[i] != prev)) {
                    ast = false;
                }
                if (!ast) j++;
                break;
        }
        console.log(s.slice(0,i+1) + ' ' + p.slice(0,j));
    }
    return true
};
```
###### Analysis
[[TODO]]: Complete attempt