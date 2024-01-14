# [[LeetCode] 392. Is Subsequence](https://leetcode.com/problems/is-subsequence/description)

## Problem

> Given two strings s and t, return true if s is a subsequence of t, or false otherwise.
>
> A subsequence of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., "ace" is a subsequence of "abcde" while "aec" is not).

## Solution

- Check edge cases.
- Count sequence index through loop.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function isSubsequence(s: string, t: string): boolean {
  if (s.length === 0) return true;
  if (s.length === t.length) return s === t;

  let sIndex = 0;
  for (const character of t) {
    if (s[sIndex] === character) sIndex++;
  }
  return sIndex === s.length;
}
```
