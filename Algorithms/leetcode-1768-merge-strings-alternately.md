# [LeetCode] 1768. Merge Strings Alternately

## Problem

> You are given two strings word1 and word2. Merge the strings by adding letters in alternating order, starting with word1. If a string is longer than the other, append the additional letters onto the end of the merged string.
> Return _the merged string_.
> [[LeetCode] 1768. Merge Strings Alternately](https://leetcode.com/problems/merge-strings-alternately/?envType=study-plan&id=programming-skills-i)

## Solution

- Simple implementation problem. Use two pointers.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function mergeAlternately(word1: string, word2: string): string {
  let merged = "";
  let [i, j] = [0, 0];
  while (i < word1.length && j < word2.length) {
    merged += word1[i] + word2[j];
    i++;
    j++;
  }
  if (i < word1.length) merged += word1.slice(i);
  if (j < word2.length) merged += word2.slice(j);
  return merged;
}
```

## Other's Solution

- All uses same approaches.
