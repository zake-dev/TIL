# [LeetCode] 53. Maximum Subarray

## Problem

> Given an integer array `nums`, find the subarray which has the largest sum and return _its sum_.
> [[LeetCode] 53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/?envType=study-plan&id=data-structure-i)

## Solution

- Use `Kadane's Algorithm`[^1] to calculate the largest sum of subarrays.
  [^1]: [[Wikipedia] Maximum Subarray Problem](https://en.wikipedia.org/wiki/Maximum_subarray_problem)
- There is no empty array input ensured by constraints.
- Basically, `Kadane's Algorithm` is kind of `Dynamic Programming Alogrithm`.
- Runtime Complexity: **O(n)**

```typescript
function maxSubArray(nums: number[]): number {
  let bestSum = -Infinity;
  let currentSum = 0;
  for (const num of nums) {
    currentSum = Math.max(num, currentSum + num);
    bestSum = Math.max(bestSum, currentSum);
  }
  return bestSum;
}
```

## Other's Solution

- `Kadane's Alogrithm` seems to be the best solution compared to others in terms of runtime complexity.
- One of those uses `Brute-Force Algorithm`.
- Runtime Complexity: **O(n^2)**

```typescript
function maxSubArray(nums: number[]): number {
  let n = nums.length;
  let maxSum = -Infinity;
  for (let i = 0; i < n; ++i) {
    let sum = nums[i];
    maxSum = Math.max(maxSum, sum);
    for (let j = i + 1; j < n; ++j) {
      sum += nums[j];
      maxSum = Math.max(maxSum.sum);
    }
  }
  return maxSum;
}
```
