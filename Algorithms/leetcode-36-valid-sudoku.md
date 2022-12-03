# [LeetCode] 36. Valid Sudoku

## Problem

> Determine if a `9 x 9` Sudoku board is valid. Only the filled cells need to be validated **according to the following rules**:
>
> 1. Each row must contain the digits `1-9` without repetition.
> 2. Each column must contain the digits `1-9` without repetition.
> 3. Each of the nine `3 x 3` sub-boxes of the grid must contain the digits `1-9` without repetition.

> Note:
>
> - A Sudoku board (partially filled) could be valid but is not necessarily solvable.
> - Only the filled cells need to be validated according to the mentioned rules.
>   [[LeetCode] 36. Valid Sudoku](https://leetcode.com/problems/valid-sudoku/?envType=study-plan&id=data-structure-i)

## Solution

- This is an implementation problem.
- Should filter `.` and parse `rows`, `columns`, `squares` to `number[]`.
- Should validate a set of sudoku numbers are _all unique_ and only contains `1-9`.
- Runtime Complexity: **O(n^2)**

```typescript
function isValidSudoku(board: string[][]): boolean {
  return (
    allValidRows(board) && allValidColumns(board) && allValidSquares(board)
  );
}

function allValidRows(board: string[][]): boolean {
  return parseRows(board).every(isValidSudokuSet);
}

function allValidColumns(board: string[][]): boolean {
  return parseColumns(board).every(isValidSudokuSet);
}

function allValidSquares(board: string[][]): boolean {
  return parseSquares(board).every(isValidSudokuSet);
}

function parseRows(board: string[][]): number[][] {
  return board.map((row) => row.filter((s) => s !== ".").map((n) => +n));
}

function parseColumns(board: string[][]): number[][] {
  const rotated = [...Array(9).keys()].map((i) =>
    board.reduce((column, row) => column.concat(row[i]), [])
  );
  return parseRows(rotated);
}

function parseSquares(board: string[][]): number[][] {
  const squares = [];
  for (let i = 0; i < 9; i += 3)
    for (let j = 0; j < 9; j += 3)
      squares.push([
        board[i][j],
        board[i][j + 1],
        board[i][j + 2],
        board[i + 1][j],
        board[i + 1][j + 1],
        board[i + 1][j + 2],
        board[i + 2][j],
        board[i + 2][j + 1],
        board[i + 2][j + 2],
      ]);
  return parseRows(squares);
}

function isValidSudokuSet(array: number[]): boolean {
  if (array.length !== new Set(array).size) return false;
  return array.every((n) => /[1-9]/g.test(n.toString()));
}
```

## Other's Solution

- These code line look way more simple.
- Use sets to check if there is a duplicate number.
- Just loop once to compute the result.
- Runtime Complexity: **O(n)**

```typescript
function isValidSudoku(board) {
  let rows = getListOfSets(board.length);
  let cols = getListOfSets(board.length);
  let boxes = getListOfSets(board.length);

  for (let i = 0; i < board.length; i++) {
    for (let j = 0; j < board[0].length; j++) {
      let c = board[i][j];

      if (c === ".") {
        continue;
      }

      let box = getBox(i, j);

      if (rows[i].has(c) || cols[j].has(c) || boxes[box].has(c)) {
        return false;
      } else {
        rows[i].add(c);
        cols[j].add(c);
        boxes[box].add(c);
      }
    }
  }

  return true;
}

const getBox = (i, j) => 3 * Math.floor(j / 3) + Math.floor(i / 3);
const getListOfSets = (n) => new Array(n).fill().map((_) => new Set());
```
