# #8. String to Integer (atoi)
## Question
Implement the `myAtoi(string s)` function, which converts a string to a 32-bit signed integer (similar to C/C++'s `atoi` function).

The algorithm for `myAtoi(string s)` is as follows:

1.  Read in and ignore any leading whitespace.
2.  Check if the next character (if not already at the end of the string) is `'-'` or `'+'`. Read this character in if it is either. This determines if the final result is negative or positive respectively. Assume the result is positive if neither is present.
3.  Read in next the characters until the next non-digit character or the end of the input is reached. The rest of the string is ignored.
4.  Convert these digits into an integer (i.e. `"123" -> 123`, `"0032" -> 32`). If no digits were read, then the integer is `0`. Change the sign as necessary (from step 2).
5.  If the integer is out of the 32-bit signed integer range `[-231, 231 - 1]`, then clamp the integer so that it remains in the range. Specifically, integers less than `-231` should be clamped to `-231`, and integers greater than `231 - 1` should be clamped to `231 - 1`.
6.  Return the integer as the final result.

**Note:**
-   Only the space character `' '` is considered a whitespace character.
-   **Do not ignore** any characters other than the leading whitespace or the rest of the string after the digits.

###### Example 1:
```
Input: s = "42"
Output: 42
```

###### Example 2:

```
Input: s = "   -42"
Output: -42
```

###### Example 3:
```
Input: s = "4193 with words"
Output: 4193
```
###### Constraints:
-   `0 <= s.length <= 200`
-   `s` consists of English letters (lower-case and upper-case), digits (`0-9`), `' '`, `'+'`, `'-'`, and `'.'`.

---

## Solution
### Initial Solution
```typescript
function myAtoi(s: string): number {
    let strInt = '';
    let sign = null;
    let leading = true;
    
    for (let i=0; i<s.length; i++) {
        if (s[i] == ' ' && leading) continue;
        leading = false;

        if (sign == null && s[i] == '-') {
            sign = 1;
            continue;
        }
        if (sign == null && s[i] == '+') {
            sign = 0;
            continue;
        }
                
        if ((+s[i] || +s[i] == 0) && s[i] != ' ') {
            strInt = strInt + s[i];
            sign = sign==null ? 0 : sign; 
        } else {
            break;
        }
    }
    
    if (strInt == '') return 0;
    let res = parseInt(strInt);
    res = sign ? -res : res;
    res = res < -(2**31) ? -(2**31) : res;
    res = res >= 2**31 ? (2**31) - 1 : res;
    return res;
};
```

###### Analysis
- Runtime: 139 ms, faster than 36.04% of TypeScript online submissions for String to Integer (atoi).
- Memory Usage: 46.3 MB, less than 24.72% of TypeScript online submissions for String to Integer (atoi)
Not pretty but it works