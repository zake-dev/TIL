# [LeetCode] 973. K Closest Points to Origin

## Problem

> Given an array of `points` where `points[i] = [xi, yi]` represents a point on the **X-Y** plane and an integer `k`, return the `k` closest points to the origin `(0, 0)`.
> The distance between two points on the **X-Y plane** is the Euclidean distance (i.e., `√(x1 - x2)2 + (y1 - y2)2)`.
> You may return the answer in **any order**. The answer is **guaranteed** to be **unique** (except for the order that it is in).
> [[LeetCode] 973. K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Convert points to distance.
- Sort by distance.
- Pick point only.
- Slice the array `k` elements.
- Time Complexity: **O(n\*logn)**, Space Complexity: **O(n)**

```typescript
function kClosest(points: number[][], k: number): number[][] {
  return points
    .map((point) => ({ point, distance: toDistance(point) }))
    .sort((a, b) => a.distance - b.distance)
    .map(({ point }) => point)
    .slice(0, k);
}

function toDistance(point: number[]): number {
  const [x, y] = point;
  return Math.sqrt(x ** 2 + y ** 2);
}
```

## Other's Solution

- Also you can apply quick select algorithm instead of directly sorting.
- However, quick select algorithm is hard to understand for everyone including me. :(
