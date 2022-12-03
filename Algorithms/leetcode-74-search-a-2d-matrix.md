# [LeetCode] 74. Search a 2D Matrix

## Problem

> Write an efficient algorithm that searches for a value target in an m x n integer matrix matrix. This matrix has the following properties:
>
> - Integers in each row are sorted from left to right.
> - The first integer of each row is greater than the last integer of the previous row.

> [[LeetCode] 74. Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/?envType=study-plan&id=data-structure-i)

## Solution

- The size of the input constraints is small enough to use `Brute-Force Algorithm`.
  - `m == matrix.length`
  - `n == matrix[i].length`
  - `1 <= m, n <= 100`
- If the size of input get bigger, `Binary Search Alogrithm` will be more efficient because the given array is sorted already.
- Runtime Complexity: **O(n^2)**

```typescript
function searchMatrix(matrix: number[][], target: number): boolean {
  return matrix.some((row) => row.some((n) => n === target));
}
```

## Other's Solution

- Nest `Binary Search Algorithm` twice.
- Find the `row` which has range including `target`.
- Search `target` from `row` using `Binary Search Algorithm` again.
- Runtime Complexity: **O(log^2n)**

```typescript
function searchMatrix(matrix: number[][], target: number): boolean {
  let l = 0;
  let r = matrix.length - 1;

  while (l <= r) {
    const mid = Math.floor((l + r) / 2);
    const first = matrix[mid][0];
    const last = matrix[mid][matrix[mid].length - 1];
    if (target === first || target === last) return true;
    if (target > first && target < last)
      return binarySearch(matrix[mid], target);
    if (target < first) r = mid - 1;
    else l = mid + 1;
  }
  return false;
}

function binarySearch(nums: number[], target: number): boolean {
  let l = 0;
  let r = nums.length - 1;

  while (l <= r) {
    const mid = Math.floor((l + r) / 2);
    if (nums[mid] === target) return true;
    if (nums[mid] < target) l = mid + 1;
    else r = mid - 1;
  }

  return false;
}
```
