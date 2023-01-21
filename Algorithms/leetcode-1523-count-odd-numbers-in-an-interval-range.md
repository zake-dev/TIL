# [LeetCode] 1523. Count Odd Numbers in an Interval Range

## Problem

> Given two non-negative integers `low` and `high`. Return _the count of odd numbers between `low` and `high` (inclusive)_.
> [[LeetCode] 1523. Count Odd Numbers in an Interval Range](https://leetcode.com/problems/count-odd-numbers-in-an-interval-range/?envType=study-plan&id=programming-skills-i)

## Solution

- Simple calculation problem.
- Every range has `Math.floor((high - low) / 2) + 1` odd numbers, except both `high` and `low` are even numbers.
- `~~` operator is equivalent to `Math.floor` but faster.
- Time Complexity: **O(1)**, Space Complexity: **O(1)**

```typescript
function countOdds(low: number, high: number): number {
  const extra = low & 1 || high & 1 ? 1 : 0;
  return ~~((high - low) / 2) + extra;
}
```

## Other's Solution

- This is a simple implementation problem.
