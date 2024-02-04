# [[LeetCode] 73. Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/description)

# Solution - TypeScript

```typescript
function setZeroes(matrix: number[][]): void {
  const m = matrix.length;
  const n = matrix[0].length;
  const zeroRows = new Set();
  const zeroCols = new Set();
  for (let i = 0; i < m; i++)
    for (let j = 0; j < n; j++)
      if (matrix[i][j] === 0) {
        zeroRows.add(i);
        zeroCols.add(j);
      }

  for (let i = 0; i < m; i++)
    for (let j = 0; j < n; j++)
      if (zeroRows.has(i) || zeroCols.has(j)) matrix[i][j] = 0;
}
```
