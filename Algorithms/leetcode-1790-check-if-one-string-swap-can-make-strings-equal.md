# [LeetCode] 1790. Check if One String Swap Can Make Strings Equal

## Problem

> You are given two strings `s1` and `s2` of equal length. A **string swap** is an operation where you choose two indices in a string (not necessarily different) and swap the characters at these indices.
> Return _`true` if it is possible to make both strings equal by performing **at most one string swap** on **exactly one** of the strings_. Otherwise, return `false`.
> [[LeetCode] 1790. Check if One String Swap Can Make Strings Equal](https://leetcode.com/problems/check-if-one-string-swap-can-make-strings-equal/description/?envType=study-plan&id=programming-skills-i)

## Solution

- This is not an optimized solution but easy to read.
- Count how many characters are different from `s1` to `s2`.
- If the difference is smaller than `2` and also `s1` is anagram of `s2`, the result is `true`. Return `false` otherwise.
- Time Complexity: **O(n\*logn)**, Space Complexity: **O(n)**

```typescript
function areAlmostEqual(s1: string, s2: string): boolean {
  let count = 0;
  for (let i = 0; i < s1.length; i++) if (s1[i] !== s2[i]) count++;
  return count <= 2 && isAnagram(s1, s2);
}

function isAnagram(s1: string, s2: string): boolean {
  const [c1, c2] = [s1.split("").sort(), s2.split("").sort()];
  for (let i = 0; i < c1.length; i++) if (c1[i] !== c2[i]) return false;
  return true;
}
```

## Other's Solution

- Check directly in first loop.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function areAlmostEqual(s1: string, s2: string): boolean {
  if (s1 === s2) return true;

  const [c1, c2] = [s1.split(""), s2.split("")];
  const indices: number[] = [];
  for (let i = 0; i < c1.length; i++) {
    if (c1[i] !== c2[i]) indices.push(i);
    if (indices.length === 2) {
      const [i1, i2] = indices;
      [c1[i1], c1[i2]] = [c1[i2], c1[i1]];
      return c1.join("") === c2.join("");
    }
  }
  return false;
}
```
