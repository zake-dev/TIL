# [[LeetCode] 130. Surrounded Regions](https://leetcode.com/problems/surrounded-regions/description)

# Solution - TypeScript

```typescript
function solve(board: string[][]): void {
  const [m, n] = [board.length, board[0].length];

  function captureBorderLands(i: number, j: number): void {
    if (i < 0 || j < 0 || i >= m || j >= n || board[i][j] !== "O") return;
    board[i][j] = "B";
    captureBorderLands(i + 1, j);
    captureBorderLands(i - 1, j);
    captureBorderLands(i, j + 1);
    captureBorderLands(i, j - 1);
  }

  for (let i = 0; i < m; i++)
    for (let j = 0; j < n; j++)
      if (i === 0 || i === m - 1 || j === 0 || j === n - 1)
        captureBorderLands(i, j);

  for (let i = 0; i < m; i++)
    for (let j = 0; j < n; j++)
      if (board[i][j] === "B") board[i][j] = "O";
      else if (board[i][j] === "O") board[i][j] = "X";
}
```
