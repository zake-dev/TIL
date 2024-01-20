# [[LeetCode] 54. Spiral Matrix](https://leetcode.com/problems/spiral-matrix/description)

# Solution - TypeScript

```typescript
function spiralOrder(matrix: number[][]): number[] {
  const spiral: number[] = [];

  let m = matrix.length;
  let n = matrix[0].length;
  let row = 0;
  let col = 0;

  while (row < m && col < n) {
    for (let i = col; i < n && row < m; i++) spiral.push(matrix[row][i]);
    row++;
    for (let i = row; i < m && col < n; i++) spiral.push(matrix[i][n - 1]);
    n--;
    for (let i = n - 1; i >= col && row < m; i--) spiral.push(matrix[m - 1][i]);
    m--;
    for (let i = m - 1; i >= row && col < n; i--) spiral.push(matrix[i][col]);
    col++;
  }

  return spiral;
}
```
