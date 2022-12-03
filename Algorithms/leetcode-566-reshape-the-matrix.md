# [LeetCode] 566. Reshape the Matrix

## Problem

> In MATLAB, there is a handy function called `reshape` which can reshape an `m x n` matrix into a new one with a different size `r x c` keeping its original data.
> You are given an `m x n` matrix `mat` and two integers `r` and `c` representing the number of rows and the number of columns of the wanted reshaped matrix.
> The reshaped matrix should be filled with all the elements of the original matrix in the same row-traversing order as they were.
> If the `reshape` operation with given parameters is possible and legal, output the new reshaped matrix; Otherwise, output the original matrix.
> [[LeetCode] 566. Reshape the Matrix](https://leetcode.com/problems/reshape-the-matrix/)

## Solution

- Flatten the given `mat`.
- Validate the length of `mat` is equal to `r * c`.
- Slice the flattened array into the target shape.

```typescript
function matrixReshape(mat: number[][], r: number, c: number): number[][] {
  const flattened = ;
  if (flattened.length !== r * c) return mat;

  const reshaped = [];
  for (let i = 0; i < flattened.length; i += c)
    reshaped.push(flattened.slice(i, i + c));
  return reshaped;
}
```

## Other's Solution
