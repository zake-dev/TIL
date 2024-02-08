# [[LeetCode] 200. Number of Islands](https://leetcode.com/problems/number-of-islands/description)

# Solution - TypeScript

```typescript
function numIslands(grid: string[][]): number {
  const [m, n] = [grid.length, grid[0].length];
  const visited = Array.from(Array(m), () => Array(n).fill(false));

  function visitAdjacent(i: number, j: number): void {
    if (i < 0 || j < 0 || i >= m || j >= n) return;
    if (visited[i][j] || grid[i][j] === "0") return;
    visited[i][j] = true;
    visitAdjacent(i - 1, j);
    visitAdjacent(i + 1, j);
    visitAdjacent(i, j - 1);
    visitAdjacent(i, j + 1);
  }

  let count = 0;
  for (let i = 0; i < m; i++) {
    for (let j = 0; j < n; j++) {
      if (visited[i][j] || grid[i][j] === "0") continue;
      visitAdjacent(i, j);
      count++;
    }
  }

  return count;
}
```
