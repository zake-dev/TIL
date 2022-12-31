# [LeetCode] 344. Reverse String

## Problem

> Write a function that reverses a string. The input string is given as an array of characters `s`.
> You must do this by modifying the input array in-place with `O(1)` extra memory.
> [[LeetCode] 344. Reverse String](https://leetcode.com/problems/reverse-string/description/)

## Solution

- Swap left and right element moving to center.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function reverseString(s: string[]): void {
  for (let index = 0; index < s.length / 2; index++) {
    const oppositeIndex = s.length - 1 - index;
    [s[index], s[oppositeIndex]] = [s[oppositeIndex], s[index]];
  }
}
```

## Other's Solution

- This is a simple implementation problem.
