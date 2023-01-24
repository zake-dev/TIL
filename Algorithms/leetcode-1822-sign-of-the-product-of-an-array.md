# [LeetCode] 1822. Sign of the Product of an Array

## Problem

> There is a function `signFunc(x)` that returns:
>
> - `1` if `x` is positive.
> - `-1` if `x` is negative.
> - `0` if `x` is equal to `0`.
>
> You are given an integer array `nums`. Let `product` be the product of all values in the array `nums`.
> Return `signFunc(product)`.
> [[LeetCode] 1822. Sign of the Product of an Array](https://leetcode.com/problems/sign-of-the-product-of-an-array/description/?envType=study-plan&id=programming-skills-i)

## Solution

- Map the given array `nums` to sign.
- Product all signs in `nums`.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function arraySign(nums: number[]): number {
  return nums.map(toSign).reduce((a, b) => a * b);
}

function toSign(n: number): number {
  if (n > 0) return 1;
  if (n < 0) return -1;
  return 0;
}
```

## Other's Solution

- This is a simple implementation problem.
