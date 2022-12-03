# [LeetCode] 383. Rnasom Note

## Problem

> Given two strings `ransomNote` and `magazine`, return `true` _if `ransomNote` can be constructed by using the letters from `magazine` and `false` otherwise_.
> Each letter in `magazine` can only be used once in `ransomNote`.
> [[LeetCode] 383. Ransom Note](https://leetcode.com/problems/ransom-note/)

## Solution

- Create character `counter` from `ransomNote` and `magazine`.
- Check `ransomNote` is a subset of `magazine`.
- Runtime Complexity: **O(n)**

```typescript
function canConstruct(ransomNote: string, magazine: string): boolean {
  const ransomNoteCounter = toCounter(ransomNote);
  const magazineCounter = toCounter(magazine);
  return Object.entries(ransomNoteCounter).every(
    ([character, count]) => magazineCounter[character] >= count
  );
}

function toCounter(text: string): Record<string, number> {
  const counter = {};
  for (const element of text) counter[element] = (counter[element] ?? 0) + 1;
  return counter;
}
```

## Other's Solution

- Most solutions uses similar approach.
- Cannot find the logic not using `counter`.
