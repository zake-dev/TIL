# [LeetCode] 56. Merge Intervals

## Problem

> Given an array of `intervals` where `intervals[i] = [starti, endi]`, merge all overlapping intervals, and return _an array of the non-overlapping intervals that cover all the intervals in the input_.
> [[LeetCode] 56. Merge Intervals](https://leetcode.com/problems/merge-intervals/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Sort `intervals` by `lower` element.
- Iterate over intervals, keep values of `min` and `max` interval while the intervals are overlapping.
- If the range of the next interval is not overlapping, push the `[min, max]`, update `min` and `max` value.
- Runtime Complexity: **O(n*logn + n) = O(n*logn)**

```typescript
function merge(intervals: number[][]): number[][] {
  intervals.sort((a, b) => a[0] - b[0]);

  const result: number[][] = [];
  let [min, max] = intervals[0];
  for (let i = 1; i < intervals.length; i++) {
    const [lower, upper] = intervals[i];
    if (max >= lower) {
      min = Math.min(min, lower);
      max = Math.max(max, upper);
      continue;
    }
    result.push([min, max]);
    [min, max] = intervals[i];
  }
  result.push([min, max]);

  return result;
}
```

## Other's Solution

- Similar approach, but more concise.
- Push `interval` first and modify that if the next interval is overlapping.
- Runtime Complexity: **O(n\*logn)**

```typescript
function merge(intervals: number[][]): number[][] {
  intervals.sort((a, b) => a[0] - b[0]);
  const res = [];
  for (const interval of intervals) {
    if (res.length > 0 && res[res.length - 1][1] >= interval[0]) {
      res[res.length - 1][1] = Math.max(interval[1], res[res.length - 1][1]);
    } else {
      res.push(interval);
    }
  }
  return res;
}
```
