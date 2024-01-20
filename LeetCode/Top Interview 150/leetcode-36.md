# [[LeetCode] 36. Valid Sudoku](https://leetcode.com/problems/valid-sudoku/description)

# Solution - TypeScript

```typescript
function validateSudokuNumber(nums: Set<number>, num: number): boolean {
  if (nums.has(num)) return false;
  nums.add(num);
  return true;
}

function isValidSudoku(board: string[][]): boolean {
  const rows = Array.from(Array(9), () => new Set<number>());
  const cols = Array.from(Array(9), () => new Set<number>());
  const subBoxes = Array.from(Array(3), () =>
    Array.from(Array(3), () => new Set<number>())
  );

  for (let i = 0; i < 9; i++) {
    for (let j = 0; j < 9; j++) {
      if (board[i][j] === ".") continue;
      const num = +board[i][j];
      if (
        !validateSudokuNumber(rows[i], num) ||
        !validateSudokuNumber(cols[j], num) ||
        !validateSudokuNumber(
          subBoxes[Math.floor(i / 3)][Math.floor(j / 3)],
          num
        )
      )
        return false;
    }
  }
  return true;
}
```
