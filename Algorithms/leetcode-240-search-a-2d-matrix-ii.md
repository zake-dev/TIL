# [LeetCode] 240. Search a 2D Matrix II

## Problem

> Write an efficient algorithm that searches for a value `target` in an `m x n` integer matrix matrix. This `matrix` has the following properties:
>
> - Integers in each row are sorted in ascending from left to right.
> - Integers in each column are sorted in ascending from top to bottom.

> [[LeetCode] 240. Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/description/?envType=study-plan&id=data-structure-ii)

## Solution

- First plan was implementing an algorithm that uses `Binary Search` diagonally, then find the `target`. However, I wasn't able to imagine how can I handle non-square matrix such as `3 x 6` sized one.
- As the constraints of this problem is quite small enough to use `Brute-Force`, I simply find the `target` by iterating whole.
- Runtime Complexity: **O(n^2)**

```typescript
function searchMatrix(matrix: number[][], target: number): boolean {
  for (const row of matrix)
    for (const number of row) if (number === target) return true;
  return false;
}
```

## Other's Solution

- Great, understandable solution with efficiency.
- Because of the characteristics of the given `matrix`, it is ensured if the last element of the row is smaller than the `target`, the `target` does not exist in current row.
- However, if the last element of the row is bigger than the `target`, the `target` can be found in current row because smaller rows are already excepted.
- Runtime Complexity: **O(n)**

```typescript
function searchMatrix(matrix: number[][], target: number): boolean {
  let row = 0;
  let col = matrix[0]?.length ?? 0 - 1;
  while (row < matrix.length && col >= 0) {
    const current = matrix[row][col];
    if (current === target) return true;
    else if (current < target) row++;
    else col--;
  }
  return false;
}
```
