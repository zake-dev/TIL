# [LeetCode] 70. Climbing Stairs

## Problem

> You are climbing a staircase. It takes `n` steps to reach the top.
> Each time you can either climb `1` or `2` steps. In how many distinct ways can you climb to the top?
> [[LeetCode] 70. Climbing Stairs](https://leetcode.com/problems/climbing-stairs/description/)

## Solution

- Outputs follows fibonacci sequence.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function climbStairs(n: number): number {
  let [n0, n1] = [1, 1];
  for (let i = 1; i <= n; i++) [n0, n1] = [n1, n0 + n1];
  return n0;
}
```

## Other's Solution

- This is a simple implementation problem.
