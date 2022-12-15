# [LeetCode] 59. Spiral matrix II

## Problem

> Given a positive integer `n`, generate an `n x n` matrix filled with elements from `1` to `n2` in spiral order.
> [[LeetCode] 59. Spiral Matrix II](https://leetcode.com/problems/spiral-matrix-ii/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Creating a spiral matrix can be divided as two steps.
- Fill `column` in a positive order, like `(0, 0)`, `(0, 1)`, `(0, 2)`, then fill `row` in a positive order.
- After every iteration, the `direction` should be flipped over.
- Runtime Complexity: **O(n)**

```typescript
function generateMatrix(n: number): number[][] {
  const matrix: number[][] = Array.from({ length: n }, (_) => new Array(n));

  let limit = n,
    row = 0,
    column = -1,
    num = 1,
    direction = 1;
  while (num <= n * n) {
    for (let i = 0; i < limit; i++, num++) {
      column += direction;
      matrix[row][column] = num;
    }
    limit--;
    for (let j = 0; j < limit; j++, num++) {
      row += direction;
      matrix[row][column] = num;
    }
    direction *= -1;
  }

  return matrix;
}
```

## Other's Solution

- This is a simple implementation problem.
