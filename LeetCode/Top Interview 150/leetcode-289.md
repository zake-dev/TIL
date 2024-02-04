# [[LeetCode] 289. Game of Life](https://leetcode.com/problems/game-of-life/description)

# Solution - TypeScript

```typescript
function gameOfLife(board: number[][]): void {
  const m = board.length;
  const n = board[0].length;
  const LIVE = 1;
  const DEAD = 0;
  const LIVE_LIVE = -1;
  const LIVE_DEAD = -2;
  const DEAD_LIVE = -3;
  const DEAD_DEAD = -4;

  const isLive = (i: number, j: number) =>
    [LIVE, LIVE_LIVE, LIVE_DEAD].includes(board[i][j]);
  const countLiveNeighbors = (i: number, j: number) => {
    const neighbors = [
      [i - 1, j - 1],
      [i - 1, j],
      [i - 1, j + 1],
      [i, j - 1],
      [i, j + 1],
      [i + 1, j - 1],
      [i + 1, j],
      [i + 1, j + 1],
    ];
    return neighbors.reduce((count, [x, y]) => {
      if (x < 0 || y < 0 || x >= m || y >= n) return count;
      return isLive(x, y) ? count + 1 : count;
    }, 0);
  };
  const toTempNextState = (i: number, j: number) => {
    const isLiveCell = isLive(i, j);
    const lives = countLiveNeighbors(i, j);
    if (isLiveCell && (lives < 2 || lives > 3)) return LIVE_DEAD;
    if (isLiveCell && (lives === 2 || lives === 3)) return LIVE_LIVE;
    if (!isLiveCell && lives === 3) return DEAD_LIVE;
    return isLiveCell ? LIVE_LIVE : DEAD_DEAD;
  };
  const toRealNextState = (i: number, j: number) =>
    [LIVE_LIVE, DEAD_LIVE].includes(board[i][j]) ? LIVE : DEAD;

  for (let i = 0; i < m; i++)
    for (let j = 0; j < n; j++) board[i][j] = toTempNextState(i, j);

  for (let i = 0; i < m; i++)
    for (let j = 0; j < n; j++) board[i][j] = toRealNextState(i, j);
}
```
