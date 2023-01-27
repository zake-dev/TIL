# [LeetCode] 1572. Matrix Diagonal Sum

## Problem

> Given a square matrix `mat`, return the sum of the matrix diagonals.
> Only include the sum of all the elements on the primary diagonal and all the elements on the secondary diagonal that are not part of the primary diagonal.
> [[LeetCode] 1572. Matrix Diagonal Sum](https://leetcode.com/problems/matrix-diagonal-sum/?envType=study-plan&id=programming-skills-i)

## Solution

- Add up elemnts of primary diagnoal, and secondary diagonal iterating over `mat`.
- Skip if `primary` and `secondary` points same element.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function diagonalSum(mat: number[][]): number {
  const n = mat.length;
  let sum = 0;
  for (let i = 0; i < n; i++) {
    const primary = mat[i][i];
    const secondary = mat[i][n - 1 - i];
    const isDuplicate = i === n - 1 - i;
    sum += primary + (isDuplicate ? 0 : secondary);
  }
  return sum;
}
```

## Other's Solution

- This is a simple implementation problem.