# [LeetCode] 171. Excel Sheet Column Number

## Problem

> Given a string `columnTitle` that represents the column title as appears in an Excel sheet, return _its corresponding column number_.
> [[LeetCode] 171. Excel Sheet Column Number](https://leetcode.com/problems/excel-sheet-column-number/description/)

## Solution

- Excel sheet column number can be thought as a 26-base number.
- Write a converter function for each digit, and calculate the number.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function titleToNumber(columnTitle: string): number {
  let result = 0;
  for (let i = columnTitle.length - 1, base = 1; i >= 0; i--, base *= 26)
    result += alphaToNumber(columnTitle[i]) * base;
  return result;
}

function alphaToNumber(alphabet: string): number {
  return "ABCDEFGHIJKLMNOPQRSTUVWXYZ".indexOf(alphabet) + 1;
}
```

## Other's Solution

- Same solutions.
