# [LeetCode] 387. First Unique Character in String

## Problem

> Given a string `s`, _find the first non-repeating character in it and return its index_. If it does not exist, return `-1`.
> [[LeetCode] 387. First Unique Character in String](https://leetcode.com/problems/first-unique-character-in-a-string/)

## Solution

- Save the index `character` and mark as `used` that appears for the first time.
- If the character already used, delete from the `indices` and skip action.
- Return the first index value of `indices`. Map object in Javascript keeps its appended order.
- Runtime Complexity: **O(n)**

```typescript
function firstUniqChar(s: string): number {
  const indices = new Map();
  const used = new Set();
  for (let i = 0; i < s.length; i++) {
    const character = s[i];
    if (indices.has(character)) indices.delete(character);
    if (used.has(character)) continue;
    indices.set(character, i);
    used.add(character);
  }
  return indices.values().next().value ?? -1;
}
```

## Other's Solution

- Count how many times the character appears.
- Iterate over the given string again, if the count of the character is `0`, return its `index`.
- Runtime Complexity: **O(n)**

```typescript
function firstUniqChar(s: string): number {
  const counter = {};
  for (const ch of s) counter[ch] = (counter[ch] ?? 0) + 1;
  for (let i = 0; i < s.length; i++) if (counter[s[i]] === 1) return i;
  return -1;
}
```
