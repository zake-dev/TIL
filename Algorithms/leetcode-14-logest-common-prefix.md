# [LeetCode] 14. Longest Common Prefix

## Problem

> Write a function to find the longest common prefix string amongst an array of strings.
> If there is no common prefix, return an empty string `""`.
> [[LeetCode] 14. Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/description/)

## Solution

- Use Brute-Force approach. Pick a common prefix if all characters in same index in `strs` are same.
- Stop iteration if any character in same position is different all every character pointed are `undefined`.
- Time Complexity: **O(n^2)**, Space Complexity: **O(1)**

```typescript
function longestCommonPrefix(strs: string[]): string {
  let commonPrefix = "";
  let i = 0;
  while (true) {
    const target = strs[0][i];
    const allSameCharacter = strs.every((s) => s[i] === target);
    const allUndefined = strs.every((s) => s[i] === undefined);
    if (!allSameCharacter || allUndefined) break;
    commonPrefix += target;
    i++;
  }
  return commonPrefix;
}
```

## Other's Solution

- Rewritten solution based on other concept.
- Split logic as smaller functions. Compare two strings and get a common prefix of those.
- Reduce `str` in `strs` using compare function.
- More readable but not optimized because it will always loop without any break condition.
- Time Complexity: **O(n^2)**, Space Complexity: **O(1)**

```typescript
function longestCommonPrefix(strs: string[]): string {
  return strs.reduce(getCommonPrefix);
}

function getCommonPrefix(str1: string, str2: string): string {
  if (str1.length > str2.length) return getCommonPrefix(str2, str1);

  for (let i = 0; i < str1.length; i++)
    if (str1[i] !== str2[i]) return str1.substring(0, i);
  return str1;
}
```
