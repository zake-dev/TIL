# [LeetCode] 48. Rotate Image

## Problem

> You are given an `n x n` 2D `matrix` representing an image, rotate the image by **90** degrees (clockwise).
> You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. **DO NOT** allocate another 2D matrix and do the rotation.
> [[LeetCode] 48. Rotate Image](https://leetcode.com/problems/rotate-image/description/?envType=study-plan&id=data-structure-ii)

## Solution

- My approach divides the problem in a small peace. Rotating a whole `matrix` is a _sum of rotated **rings**_.
- For example, in `4 x 4` sized `matrix`, you should rotate two rings to rotate a whole `matrix`.

<table>
<td>
  <table>
  <thead>
    <tr>
      <th colspan="4">The 1<sup>st</sup> Ring</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>1</code></td>
      <td><code>2</code></td>
      <td><code>3</code></td>
      <td><code>4</code></td>
    </tr>
    <tr>
      <td><code>5</code></td>
      <td>6</td>
      <td>7</td>
      <td><code>8</code></td>
    </tr>
    <tr>
      <td><code>9</code></td>
      <td>10</td>
      <td>11</td>
      <td><code>12</code></td>
    </tr>
    <tr>
      <td><code>13</code></td>
      <td><code>14</code></td>
      <td><code>15</code></td>
      <td><code>16</code></td>
    </tr>
  </tbody>
  </table>
</td>
<td>
  <table>
  <thead>
    <tr>
      <th colspan="4">The 2<sup>nd</sup> Ring</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>2</td>
      <td>3</td>
      <td>4</td>
    </tr>
    <tr>
      <td>5</td>
      <td><code>6</code></td>
      <td><code>7</code></td>
      <td>8</td>
    </tr>
    <tr>
      <td>9</td>
      <td><code>10</code></td>
      <td><code>11</code></td>
      <td>12</td>
    </tr>
    <tr>
      <td>13</td>
      <td>14</td>
      <td>15</td>
      <td>16</td>
    </tr>
  </tbody>
  </table>
</td>
</table>

- In every ring, there are groups of 4, which should be rotated.

<table>
<td>
  <table>
  <thead>
    <tr>
      <th colspan="4">1<sup>st</sup> Ring: Group1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>1</code></td>
      <td>2</td>
      <td>3</td>
      <td><code>4</code></td>
    </tr>
    <tr>
      <td>5</td>
      <td>6</td>
      <td>7</td>
      <td>8</td>
    </tr>
    <tr>
      <td>9</td>
      <td>10</td>
      <td>11</td>
      <td>12</td>
    </tr>
    <tr>
      <td><code>13</code></td>
      <td>14</td>
      <td>15</td>
      <td><code>16</code></td>
    </tr>
  </tbody>
  </table>
</td>
<td>
  <table>
  <thead>
    <tr>
      <th colspan="4">1<sup>st</sup> Ring: Group2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td><code>2</code></td>
      <td>3</td>
      <td>4</td>
    </tr>
    <tr>
      <td>5</td>
      <td>6</td>
      <td>7</td>
      <td><code>8</code></td>
    </tr>
    <tr>
      <td><code>9</code></td>
      <td>10</td>
      <td>11</td>
      <td>12</td>
    </tr>
    <tr>
      <td>13</td>
      <td>14</td>
      <td><code>15</code></td>
      <td>16</td>
    </tr>
  </tbody>
  </table>
</td>

<td>
  <table>
  <thead>
    <tr>
      <th colspan="4">1<sup>st</sup> Ring: Group3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>2</td>
      <td><code>3</code></td>
      <td>4</td>
    </tr>
    <tr>
      <td><code>5</code></td>
      <td>6</td>
      <td>7</td>
      <td>8</td>
    </tr>
    <tr>
      <td>9</td>
      <td>10</td>
      <td>11</td>
      <td><code>12</code></td>
    </tr>
    <tr>
      <td>13</td>
      <td><code>14</code></td>
      <td>15</td>
      <td>16</td>
    </tr>
  </tbody>
  </table>
</td>
</table>

- Rotate those group elements with _destructuring syntax_.
- Runtime Complexity: **O(n^2)**, Space Complexity: **O(1)**

```typescript
function rotate(matrix: number[][]): void {
  for (let start = 0; start < matrix.length / 2; start++) {
    const end = matrix.length - 1;
    for (let offset = start; offset < end - start; offset++)
      [
        matrix[start][offset],
        matrix[offset][end - start],
        matrix[end - start][end - offset],
        matrix[end - offset][start],
      ] = [
        matrix[end - offset][start],
        matrix[start][offset],
        matrix[offset][end - start],
        matrix[end - start][end - offset],
      ];
  }
}
```

## Other's Solution

- Similar to mine. Only differences are other solutions use `while` statement instead of `for` statement.
