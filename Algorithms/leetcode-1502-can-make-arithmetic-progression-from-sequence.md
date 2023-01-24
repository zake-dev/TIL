# [LeetCode] 1502. Can Make Arithmetic Progression From Sequence

## Problem

> A sequence of numbers is called an **arithmetic progression** if the difference between any two consecutive elements is the same.
> Given an array of numbers `arr`, return _`true` if the array can be rearranged to form an **arithmetic progression**. Otherwise, return `false`_.
> [[LeetCode] 1502. Can Make Arithmetic Progression From Sequence](https://leetcode.com/problems/can-make-arithmetic-progression-from-sequence/description/?envType=study-plan&id=programming-skills-i)

## Solution

- Sort `arr` and find `difference` of sequence.
- Check all difference between numbers in sequence are equal.
- Time Complexity: **O(n\*logn)**, Space Complexity: **O(1)**

```typescript
function canMakeArithmeticProgression(arr: number[]): boolean {
  if (arr.length <= 2) return true;

  arr.sort((a, b) => a - b);
  const difference = arr[1] - arr[0];
  for (let i = 1; i < arr.length - 1; i++)
    if (arr[i + 1] - arr[i] !== difference) return false;
  return true;
}
```

## Other's Solution

- No other optimized solution exists.
