# [LeetCode] 1232. Check If It is a Straight Line

## Problem

> You are given an array `coordinates`, `coordinates[i] = [x, y]`, where `[x, y]` represents the coordinate of a point. Check if these points make a straight line in the XY plane.
> [[LeetCode] 1232. Check If It is a Straight Line](https://leetcode.com/problems/check-if-it-is-a-straight-line/description/?envType=study-plan&id=programming-skills-i)

## Solution

- Not an optimized solution.
- Sort `coordinates` first.
- Calculate a target slope from `coordinates[0]` and `coordinates[1]`.
- Check every pair sequence of points in `coordinates` has same slope.
- Time Complexity: **O(n\*logn)**, Space Complexity: **O(n)**

```typescript
function checkStraightLine(coordinates: number[][]): boolean {
  if (coordinates.length <= 2) return true;

  coordinates.sort(([xA, yA], [xB, yB]) => (xA !== xB ? xA - xB : yA - yB));

  const slope = calculateSlope(coordinates[0], coordinates[1]);
  for (let i = 1; i < coordinates.length - 1; i++) {
    const nextSlope = calculateSlope(coordinates[i], coordinates[i + 1]);
    if (slope !== nextSlope) return false;
  }
  return true;
}

function calculateSlope(pointA: number[], pointB: number[]) {
  const [[xA, yA], [xB, yB]] = [pointA, pointB];
  return (yB - yA) / (xB - xA);
}
```

## Other's Solution

- We can optimize above solution to have `O(n)` time complexity by modifying `calculateSlope` function.
- Now `caculateSlope` will work properly regardless which point is bigger than other.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function checkStraightLine(coordinates: number[][]): boolean {
  if (coordinates.length <= 2) return true;

  const slope = calculateSlope(coordinates[0], coordinates[1]);
  for (let i = 1; i < coordinates.length - 1; i++) {
    const nextSlope = calculateSlope(coordinates[i], coordinates[i + 1]);
    if (slope !== nextSlope) return false;
  }
  return true;
}

function calculateSlope(pointA: number[], pointB: number[]) {
  const [[xA, yA], [xB, yB]] = [pointA, pointB];
  if (xB < xA || yB < yA) return calculateSlope(pointB, pointA);
  return (yB - yA) / (xB - xA);
}
```
