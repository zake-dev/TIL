# [[LeetCode] 57. Insert Interval](https://leetcode.com/problems/insert-interval/description)

# Solution - TypeScript

```typescript
function insert(intervals: number[][], newInterval: number[]): number[][] {
  if (intervals.length === 0) return [newInterval];

  intervals.push(newInterval);
  intervals.sort((a, b) => a[0] - b[0]);

  const merged: number[][] = [];

  let [start, end] = intervals[0];
  for (const [nextStart, nextEnd] of intervals) {
    if (end >= nextStart) {
      end = Math.max(end, nextEnd);
      continue;
    }
    merged.push([start, end]);
    [start, end] = [nextStart, nextEnd];
  }
  merged.push([start, end]);

  return merged;
}
```
