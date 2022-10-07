# #6. Zigzag Conversion
#lc/medium #lc/success

## Question
The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)
```
P   A   H   N
A P L S I I G
Y   I   R
```

And then read line by line: `"PAHNAPLSIIGYIR"`

Write the code that will take a string and make this conversion given a number of rows:

string convert(string s, int numRows);

###### Example 1:
```
Input: s = "PAYPALISHIRING", numRows = 3
Output: "PAHNAPLSIIGYIR"
```

###### Example 2:
```
Input: s = "PAYPALISHIRING", numRows = 4
Output: "PINALSIGYAHRPI"
Explanation:
P     I    N
A   L S  I G
Y A   H R
P     I
```

###### Example 3:
```
Input: s = "A", numRows = 1
Output: "A"
```

###### Constraints:
-   `1 <= s.length <= 1000`
-   `s` consists of English letters (lower-case and upper-case), `','` and `'.'`.
-   `1 <= numRows <= 1000`

---
## Solution
### Initial Solution
- Store each input row as a row in a 2D array. Start at row 0 (row 1 in the zigzag) and add the first character. Go to row 2 and add the second character, and repeat until the number of rows needed is hit. Then reverse back up the array, adding the characters until the top is hit. Reverse back down and repeat until the string is used up.
- Add the characters by row.
```typescript
function convert(s: string, numRows: number): string {
    // 2D array
    let zz = [...Array(numRows)];
    let row = 0;
    let dir = 1;    // direction to traverse zigzag array (forward/backward)
    
    for (let i=0; i<s.length; i++) {        
        // append char to array row
        if (zz[row]) {
            zz[row].push(s[i]);
        } else {
            zz[row] = [s[i]];
        }
        
        // increment/decrement array row
        dir ? row++ : row--;
        
        // update dir flag
        dir = (row == numRows-1) ? 0 : dir;
        dir = (row == 0) ? 1 : dir;
    }
    
    // combine array rows
    return zz.flat().join("");
};
```

###### Analysis
> [!success]
> - Runtime: 190 ms, faster than 25.55% of TypeScript online submissions for Zigzag Conversion.
> - Memory Usage: 50.9 MB, less than 25.96% of TypeScript online submissions for Zigzag Conversion.

## Leetcode Solution 1: Sort by Row
Basically same approach as my solution

###### Intuition
By iterating through the string from left to right, we can easily determine which row in the Zig-Zag pattern that a character belongs to.

###### Algorithm
Iterate through `s` from left to right, appending each character to the appropriate row. The appropriate row can be tracked using two variables: the current row and the current direction.

The current direction changes only when we moved up to the topmost row or moved down to the bottommost row.