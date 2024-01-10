# [LeetCode] 1768. Merge Strings Alternately

## Problem

> You are given two strings word1 and word2. Merge the strings by adding letters in alternating order, starting with word1. If a string is longer than the other, append the additional letters onto the end of the merged string.
> Return _the merged string_.
> [[LeetCode] 1768. Merge Strings Alternately](https://leetcode.com/problems/merge-strings-alternately/description/?envType=study-plan-v2&envId=leetcode-75)

## Solution

- With a single pointer, push each character from both strings. Keep extracting characters until reaching end of the longer word.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function mergeAlternately(word1: string, word2: string): string {
  const merged: string[] = [];
  for (let i = 0; i < word1.length || i < word2.length; i++) {
    if (i < word1.length) merged.push(word1[i]);
    if (i < word2.length) merged.push(word2[i]);
  }
  return merged.join('');
};
```
