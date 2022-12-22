# [LeetCode] 49. Group Anagrams

## Problem

> Given an array of strings `strs`, group **the anagrams** together. You can return the answer in **any order**.
> An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.
> [[LeetCode] 49. Group Anagrams](https://leetcode.com/problems/group-anagrams/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Create a hash table that stores a group of anagram. `key` of the hash table will be the sorted text.
- Push all `str` in `strs` into the hash table.
- Return `values` of the hash table.
- Time Complexity: **O(n\*logn)**, Space Complexity: **O(n)**

```typescript
function groupAnagrams(strs: string[]): string[][] {
  const groups = new Map<string, string[]>();
  for (const str of strs) {
    const sorted = getSortedText(str);
    if (!groups.has(sorted)) groups.set(sorted, []);
    groups.get(sorted).push(str);
  }
  return [...groups.values()];
}

function getSortedText(s: string): string {
  return s.split("").sort().join();
}
```

## Other's Solution

- Similar approaches. No other intuitive solution exists.
