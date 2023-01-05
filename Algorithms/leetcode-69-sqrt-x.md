# [LeetCode] 69. Sqrt(x)

## Problem

> Given a non-negative integer `x`, return _the square root of `x` rounded down to the nearest integer_. The returned integer should be **non-negative** as well.
> You **must not use** any built-in exponent function or operator.
> For example, do not use `pow(x, 0.5)` in c++ or `x ** 0.5` in python.
> [[LeetCode] 69. Sqrt(x)](https://leetcode.com/problems/sqrtx/description/)

## Solution

- Brute-Force approach to find the square root of the given `x`.
- Break iteration if the square root is found.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function mySqrt(x: number): number {
  let sqrt = 0;
  while (true) {
    if (sqrt * sqrt === x) return sqrt;
    if (sqrt * sqrt > x) return sqrt - 1;
    sqrt++;
  }
  return sqrt;
}
```

## Other's Solution

- We're looking for a square root in the range of `0` to the given `x`. The range of numbers can be thought as sorted array, so we can apply binary search as well.
- Time Complexity: **O(logn)**, Space Complexity: **O(1)**

```typescript
function mySqrt(x: number): number {
  let [left, right] = [0, x];
  while (left < right) {
    const center = ~~((left + right) / 2);
    const squared = center * center;
    if (squared === x) return center;
    if (squared > x) right = center - 1;
    else left = center + 1;
  }
  return x < right * right ? right - 1 : right;
}
```
