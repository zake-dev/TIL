# [LeetCode] 202. Happy Number

## Problem

> Write an algorithm to determine if a number `n` is happy.
> A **happy number** is a number defined by the following process:
>
> - Starting with any positive integer, replace the number by the sum of the squares of its digits.
> - Repeat the process until the number equals 1 (where it will stay), or it **loops endlessly in a cycle** which does not include 1.
> - Those numbers for which this process **ends in** 1 are happy.
>
> Return _`true` if `n` is a happy number, and `false` if not_.
> [[LeetCode] 202. Happy Number](https://leetcode.com/problems/happy-number/description/)

## Solution

- Write a helper function that finds next number of sequence.
- Check next number until it reaches `1` or any numbers already in cycle, break the loop.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function isHappy(n: number): boolean {
  const cycle = new Set();
  while (!cycle.has(n)) {
    if (n === 1) return true;
    cycle.add(n);
    n = sumOfSquaredDigits(n);
  }
  return false;
}

function sumOfSquaredDigits(n: number): number {
  return toDigits(n)
    .map((digit) => digit * digit)
    .reduce((a, b) => a + b);
}

function toDigits(n: number): number[] {
  return n
    .toString()
    .split("")
    .map((s) => +s);
}
```

## Other's Solution

- Some optimized version of solution exist but basically they use same logic.
