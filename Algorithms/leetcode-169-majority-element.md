# [LeetCode] 169. Majority Element

## Problem

> Given an array `nums` of size `n`, return _the majority element_.
> The majority element is the element that appears more than `⌊n / 2⌋` times. You may assume that the majority element always exists in the array.
> [[LeetCode] 169. Majority Element](https://leetcode.com/problems/majority-element/description/?envType=study-plan&id=data-structure-ii)

## Solution

- I failed to find how to solve this problem in linear time with O(1) space.
- Make a `counter` from the given `nums`, then find the maximum `key` from the `counter`.
- Runtime Complexity: **O(n)**

```typescript
function majorityElement(nums: number[]): number {
  const counter = new Map<number, number>();
  for (const num of nums) counter.set(num, (counter.get(num) ?? 0) + 1);
  console.log([...counter.entries()]);
  return [...counter.entries()].reduce((max, item) =>
    max[1] < item[1] ? item : max
  )[0];
}
```

## Other's Solution

- Solution which uses O(1) space only.
- To be the majority element, it should appear at least `n / 2` times. Therefore, the `count` of the majority element will always bigger than `0`.
- Runtime Complexity: **O(n)**

```typescript
function majorityElement(nums: number[]): number {
  let result = nums[0];
  let count = 0;

  for (const num of nums) {
    if (!count) result = num;
    count += result === num ? 1 : -1;
  }

  return result;
}
```
