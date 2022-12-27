# [LeetCode] 191. Number of 1 Bits

## Problem

> Write a function that takes an unsigned integer and returns the number of '1' bits it has (also known as the Hamming weight).
> **Note:**
>
> - Note that in some languages, such as Java, there is no unsigned integer type. In this case, the input will be given as a signed integer type. It should not affect your implementation, as the integer's internal binary representation is the same, whether it is signed or unsigned.

> [[LeetCode] 191. Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/description/)

## Solution

- Use bit operators `>>>` and `&`.
- if `n & 1 === true`, the last binary digit of the `nums` is `1`.
- `>>>` operator will drop last binary digit in `nums`.
- Below is recursive version of solution. You can optimize the recursive function with memoization technique to reduce time when this function is called many times.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function hammingWeight(n: number): number {
  function recursiveHammingWeight(n: number, count: number): number {
    if (n === 0) return count;
    return recursiveHammingWeight(n >>> 1, n & 1 ? count + 1 : count);
  }

  return recursiveHammingWeight(n, 0);
}
```

## Other's Solution

- You can use naive function call with built-in function.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function hammingWeight(n: number): number {
  return n.toString(2).split("0").join("").length;
}
```
