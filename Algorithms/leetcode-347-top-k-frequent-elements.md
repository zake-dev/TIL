# [LeetCode] 347. Top K Frequent Elements

## Problem

> Given an integer array `nums` and an integer `k`, return _the `k` most frequent elements_. You may return the answer in **any order**.
> [[LeetCode] 347. Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/description/)

## Solution

- Count frequencies using `Map`.
- Sort `counter` by its frequency in descending order.
- Take `key` of `counter` only, slice it to size `k`.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function topKFrequent(nums: number[], k: number): number[] {
  return [...toCounter(nums).entries()]
    .sort((a, b) => b[1] - a[1])
    .map(([key, _]) => key)
    .slice(0, k);
}

function toCounter(nums: number[]): Map<number, number> {
  const counter = new Map<number, number>();
  for (const num of nums) {
    const count = (counter.get(num) ?? 0) + 1;
    counter.set(num, count);
  }
  return counter;
}
```

## Other's Solution

- No other brilliant solution found.
