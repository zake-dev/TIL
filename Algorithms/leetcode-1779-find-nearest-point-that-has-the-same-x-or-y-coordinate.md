# [LeetCode] 1779. Find Nearest Point That Has the Same X or Y Coordinate

## Problem

> You are given two integers, `x` and `y`, which represent your current location on a Cartesian grid: `(x, y)`. You are also given an array `points` where each `points[i] = [ai, bi]` represents that a point exists at `(ai, bi)`. A point is **valid** if it shares the same x-coordinate or the same y-coordinate as your location.
> Return _the index **(0-indexed)** of the **valid** point with the smallest **Manhattan distance** from your current location_. If there are multiple, return the valid point with the **smallest** index. If there are no valid points, return `-1`.
> The **Manhattan distance** between two points `(x1, y1)` and `(x2, y2)` is `abs(x1 - x2) + abs(y1 - y2)`.
> [[LeetCode] 1779. Find Nearest Point That has the Same X or Y Coordinate](https://leetcode.com/problems/find-nearest-point-that-has-the-same-x-or-y-coordinate/description/?envType=study-plan&id=programming-skills-i)

## Solution

- While iterating over `points`, compare distance of the point and `minDistance` whenever `x === a || y === b`.
- If the computed distance is smaller than current `minDistance`, update `minIndex` as well.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function nearestValidPoint(x: number, y: number, points: number[][]): number {
  let minIndex = -1;
  let minDistance = Infinity;
  for (let i = 0; i < points.length; i++) {
    const [a, b] = points[i];
    if (x === a || y === b) {
      const distance = Math.abs(x - a) + Math.abs(y - b);
      if (distance < minDistance) {
        minIndex = i;
        minDistance = distance;
      }
    }
  }
  return minIndex;
}
```

## Other's Solution

- No other optimized or better solution I think.
