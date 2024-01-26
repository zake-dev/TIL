# [[LeetCode] 56. Merge Intervals](https://leetcode.com/problems/merge-intervals/description)

# Solution - TypeScript

```typescript
function merge(intervals: number[][]): number[][] {
  intervals.sort((a, b) => a[0] - b[0]);

  const merged: number[][] = [];
  let [start, end] = intervals[0];
  for (const [low, high] of intervals) {
    if (end >= low) {
      end = Math.max(end, high);
      continue;
    }
    merged.push([start, end]);
    [start, end] = [low, high];
  }
  merged.push([start, end]);

  return merged;
}
```
