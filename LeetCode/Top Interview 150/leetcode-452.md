# [[LeetCode] 452. Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/description)

# Solution - TypeScript

```typescript
function findMinArrowShots(points: number[][]): number {
  points.sort((a, b) => a[0] - b[0]);

  const merged: number[][] = [];

  let [start, end] = points[0];
  for (const [nextStart, nextEnd] of points) {
    if (end >= nextStart) {
      start = Math.max(start, nextStart);
      end = Math.min(end, nextEnd);
      continue;
    }
    merged.push([start, end]);
    [start, end] = [nextStart, nextEnd];
  }
  merged.push([start, end]);

  return merged.length;
}
```
