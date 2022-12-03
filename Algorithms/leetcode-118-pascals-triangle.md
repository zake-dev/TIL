# [LeetCode] 118. Pascal's Triangle

## Problem

> Given an integer `numRows`, return the first numRows of **Pascal's triangle**.
> [[LeetCode] 118. Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/?envType=study-plan&id=data-structure-i)

## Solution

- Create `row` filled with `1`.
- Manually calcualte value of `row` with index.

```typescript
function generate(numRows: number): number[][] {
  const triangle = [];
  for (let i = 0; i < numRows; i++) {
    const row = new Array(i + 1).fill(1);
    for (let j = 1; j < i; j++)
      row[j] = triangle[i - 1][j - 1] + triangle[i - 1][j];
    triangle.push(row);
  }
  return triangle;
}
```

## Other's Solution

- This is an simple implementation problem.
- Other solutions are simialr to mine.
