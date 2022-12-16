# [LeetCode] 435. Non-overlapping Intervals

## Problem

> Given an array of intervals `intervals` where `intervals[i] = [starti, endi]`, return _the minimum number of intervals you need to remove to make the rest of the intervals non-overlapping_.
> [[LeetCode] 435. Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Use `Greedy Algorithm` to solve.
- Sort `intervals` by start of the interval, `interval[0]`.
- If `previous` interval and current `interval` is overlapping, take interval having smaller point of the last interval, `interval[1]`. Because we only check `interval[1]` of `previous` and `interval[0]` of current `interval` is overlapping.
- Runtime Complexity: **O(n*logn) + O(n) = O(n*logn)**

```typescript
function eraseOverlapIntervals(intervals: number[][]): number {
  intervals.sort((a, b) => a[0] - b[0]);

  let count = 0;
  let previousInterval = [-Infinity, -Infinity];
  for (const interval of intervals) {
    if (isOverlapping(previousInterval, interval)) {
      previousInterval = getSmallerInterval(previousInterval, interval);
      count++;
      continue;
    }
    previousInterval = interval;
  }

  return count;
}

function isOverlapping(a: number[], b: number[]): boolean {
  return a[1] > b[0];
}

function getSmallerInterval(a: number[], b: number[]): number[] {
  if (a[1] < b[1]) return a;
  return b;
}
```

## Other's Solution

- Same logic but more concise.
- Sort by last element instead of the first.
- Check the previous border is overlapping to current.
- Runtime Complexity: **O(n\*logn)**

```typescript
function eraseOverlapIntervals(intervals: number[][]): number {
  intervals.sort((a, b) => a[1] - b[1]);

  let count = 0;
  let border = -Infinity;
  for (const interval of intervals) {
    if (interval[0] < border) count++;
    else border = interval[1];
  }

  return count;
}
```
