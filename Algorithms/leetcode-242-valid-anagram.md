# [LeetCode] 242. Valid Anagram

## Problem

> Given two strings `s` and `t`, return `true` _if `t` is an anagram of `s`, and `false` otherwise_.
> An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.
> [[LeetCode] 242. Valid Anagram](https://leetcode.com/problems/valid-anagram/?envType=study-plan&id=data-structure-i)

## Solution

- Sort two given strings `s` and `t`.
- Return the sorted strings are same or not.
- If there is enough memory space and needs to improve in terms of speed, use `counter` for solution.
- I splitted functions just for readability.
- Runtime Complexity: **O(n\*logn)**

```typescript
function isAnagram(s: string, t: string): boolean {
  return sortedString(s) === sortedString(t);
}

function sortedString(text: string) {
  return [...text].sort().join("");
}
```

## Other's Solution

- Solution using `counter` logic.
- Runtime Complexity: **O(n)**

```typescript
function isAnagram(s: string, t: string): boolean {
  const count = {};
  for (let char of s) {
    if (!count[char]) {
      count[char] = 0;
    }
    count[char]++;
  }

  for (let char of t) {
    if (count[char] === undefined) {
      return false;
    } else {
      count[char]--;
    }
  }

  for (let char in count) {
    if (count[char] !== 0) {
      return false;
    }
  }

  return true;
}
```
