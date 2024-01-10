# [[LeetCode] 1071. Greatest Common Divisor of Strings](https://leetcode.com/problems/greatest-common-divisor-of-strings/description/)

## Problem

> For two strings `s` and `t`, we say "`t` divides `s`" if and only if `s = t + ... + t` (i.e., `t` is concatenated with itself one or more times).
>
> Given two strings `str1` and `str2` return _the largest string `x` such that `x` divides both `str1` and `str2`_.

## Solution

- Following Euclidean algorithm, but modify it for strings.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function gcdOfStrings(str1: string, str2: string): string {
    if (str1.length < str2.length) return gcdOfStrings(str2, str1);
    if (!str1.startsWith(str2)) return '';
    for (let i = 0; i < str1.length; i += str2.length) {
      if (str1.slice(i, str2.length) !== str2) return gcdOfStrings(str2, str1.slice(i));
    }
    return str2;
};
```
