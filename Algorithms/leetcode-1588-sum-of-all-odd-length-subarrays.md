# [LeetCode] 1588. Sum of All Odd Length Subarrays

## Problem

> Given an array of positive integers `arr`, return _the sum of all possible **odd-length subarrays** of `arr`_.
> A **subarray** is a contiguous subsequence of the array.
> [[LeetCode] 1588. Sum of All Odd Length Subarrays](https://leetcode.com/problems/sum-of-all-odd-length-subarrays/description/?envType=study-plan&id=programming-skills-i)

## Solution

- Brute-Force algorithm.
- Calculated all sum of odd-length subarrays by looping.
- Time Complexity: **O(n^3)**, Space Complexity: **O(n)**

```typescript
function sumOddLengthSubarrays(arr: number[]): number {
  let sum = 0;
  for (let i = 0; i < arr.length; i++)
    for (let j = i; j < arr.length; j += 2)
      sum += sumArray(arr.slice(i, j + 1));
  return sum;
}

function sumArray(nums: number[]): number {
  return nums.reduce((a, b) => a + b);
}
```

## Other's Solution

- Optimized and neat solution based on statistical knowledge.
- Add `element * frequencies in odd-length subarrays` on a single loop.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function sumOddLengthSubarrays(arr: number[]): number {
  let sum = 0;
  for (let i = 0; i < arr.length; i++) {
    const frequency = Math.ceil(((i + 1) * (arr.length - i)) / 2);
    sum += arr[i] * frequency;
  }
  return sum;
}
```
