# [LeetCode] 976. Largest Perimeter Triangle

## Problem

> Given an integer array `nums`, return _the largest perimeter of a triangle with a non-zero area, formed from three of these lengths_. If it is impossible to form any triangle of a non-zero area, return `0`.
> [[LeetCode] 976. Largest Perimeter Triangle](https://leetcode.com/problems/find-nearest-point-that-has-the-same-x-or-y-coordinate/submissions/883367224/?envType=study-plan&id=programming-skills-i)

## Solution

- Problem asks to find the largest three points `a, b, c` in the given array `nums` that `a < b + c`.
- Sort `nums` in non-descending order.
- Iterating over 3-nested loops, escape whenever the targets are found.
- Time Complexity: **O(n\*longn)**, Space Complexity: **O(1)**

```typescript
function largestPerimeter(nums: number[]): number {
  nums.sort((a, b) => b - a);
  for (let i = 0; i < nums.length - 2; i++) {
    if (nums[i] >= nums[i + 1] + nums[i + 2]) continue;
    for (let j = i + 1; j < nums.length - 1; j++) {
      if (nums[i] >= nums[j] + nums[j + 1]) continue;
      for (let k = j + 1; k < nums.length; k++) {
        if (nums[i] < nums[j] + nums[k]) return nums[i] + nums[j] + nums[k];
      }
    }
  }
  return 0;
}
```

## Other's Solution

- After sorting `nums`, actually we don't need nested loops.
- Time Complexity: **O(n\*logn)**, Space Complexity: **O(1)**

```typescript
function largestPerimeter(nums: number[]): number {
  nums.sort((a, b) => b - a);
  for (let i = 0; i < nums.length - 2; i++) {
    const [a, b, c] = [nums[i], nums[i + 1], nums[i + 2]];
    if (a < b + c) return a + b + c;
  }
  return 0;
}
```
