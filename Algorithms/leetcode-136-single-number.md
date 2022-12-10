# [LeetCode] 136. Single Number

## Problem

> Given a **non-empty** array of integers `nums`, every element appears twice except for one. Find that single one.
> You must implement a solution with a linear runtime complexity and use only constant extra space.
> [[LeetCode] 136. Single Number](https://leetcode.com/problems/single-number/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Bitwise operator `^` returns XOR value of two operands.
- `0 ^ 5 ^ 5 = 0` use this rule to solve.
- Runtime Complexity: **O(n)**

```typescript
function singleNumber(nums: number[]): number {
  return nums.reduce((result, num) => result ^ num, 0);
}
```

## Other's Solution

- No other brilliant solution I found.
