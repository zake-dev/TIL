# [LeetCode] 451. Sort Characters By Frequency

## Problem

> Given a string `s`, sort it in **decreasing order** based on the **frequency** of the characters. The **frequency** of a character is the number of times it appears in the string.
> Return _the sorted string_. If there are multiple answers, return any of them.
> [[LeetCode] 451. Sort Characters By Frequency](https://leetcode.com/problems/sort-characters-by-frequency/description/?envType=study-plan&id=data-structure-ii)

## Solution

- This is not an optimized solution but easy to understand.
- Count how many times each character appears, and sort by its count.
- Leave character only and join it.
- Only the edge case is put same characters together in the sorted array.
- Time Complexity: **O(n\*logn)**, Space Complexity: **O(n)**

```typescript
function frequencySort(s: string): string {
  const counter = toCounter(s);
  return s
    .split("")
    .map((character) => ({ character, count: counter.get(character) }))
    .sort((a, b) => {
      if (a.count === b.count) return a.character.localeCompare(b.character);
      return b.count - a.count;
    })
    .map(({ character }) => character)
    .join("");
}

function toCounter(text: string): Map<string, number> {
  const counter = new Map<string, number>();
  for (const character of text) {
    const count = (counter.get(character) ?? 0) + 1;
    counter.set(character, count);
  }
  return counter;
}
```

## Other's Solution

- Without creating new counter array with duplicate character values, convert directly.
- Time Complexity: **O(n\*logn)**, Space Complexity: **O(n)**

```typescript
function frequencySort(s: string): string {
  const counter = toCounter(s);
  return [...toCounter(s).entries()]
    .sort((a, b) => b[1] - a[1])
    .map(([character, count]) => character.repeat(count))
    .join("");
}

function toCounter(text: string): Map<string, number> {
  const counter = new Map<string, number>();
  for (const character of text) {
    const count = (counter.get(character) ?? 0) + 1;
    counter.set(character, count);
  }
  return counter;
}
```
