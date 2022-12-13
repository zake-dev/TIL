# [LeetCode] Pascal's Triangle II

## Problem

> Given an integer `rowIndex`, return the `rowIndexth` **(0-indexed)** row of the **Pascal's triangle**.
> [[LeetCode] Pascal's Triangle II](https://leetcode.com/problems/pascals-triangle-ii/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Each coefficient of row of the **Pascal's triangle** can be computed with a formula named `Binomial Theorem`.
- Use `factorial` and `combination` as util functions.
- Runtime Complexity: **O(n)**

```typescript
function getRow(rowIndex: number): number[] {
  return Array.from({ length: rowIndex + 1 }, (_, index) =>
    combination(rowIndex, index)
  );
}

function factorial(n: number): number {
  if (n <= 1) return 1;
  return n * factorial(n - 1);
}

function combination(n: number, r: number): number {
  return factorial(n) / (factorial(r) * factorial(n - r));
}
```

## Other's Solution

- There is no other solution using zero-extra space to solve this.
- If you want to improve the function in terms of the speed, memoize the values computed from `factorial`.
