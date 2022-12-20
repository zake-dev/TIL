# [LeetCode] 409. Longest Palindrome

## Problem

> Given a string `s` which consists of lowercase or uppercase letters, return the length of _the **longest palindrome** that can be built with those letters_.
> Letters are **case sensitive**, for example, `"Aa"` is not considered a palindrome here.
> [[LeetCode] 409. Longest Palindrome](https://leetcode.com/problems/longest-palindrome/description/?envType=study-plan&id=data-structure-ii)

## Solution

- To make a palindrome, we need a pairs of characters and optional single character.
- Use hash set to track which character has a duplicate pair in the given string.
- If there is a duplicate character already, add `count` twice.
- Runtime Complexity: **O(n)**

```typescript
function longestPalindrome(s: string): number {
  const characters = new Set();
  let count = 0;
  for (const character of s) {
    if (characters.has(character)) {
      characters.delete(character);
      count += 2;
      continue;
    }
    characters.add(character);
  }
  return +(characters.size > 0) + count;
}
```

## Other's Solution

- Some other solutions use hash map instead of hash set to track character pairs, but I don't think we need a real count of how many times the character appears in. Hash set is enough to check the pair.
