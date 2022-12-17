# [LeetCode] 334. Increasing Triplet Subsequence

## Problem

> Given an integer array `nums`, return `true` _if there exists a triple of indices `(i, j, k)` such that `i < j < k` and `nums[i] < nums[j] < nums[k]`_. If no such indices exists, return `false`.
> [[LeetCode] 334. Increasing Triplet Subsequence](https://leetcode.com/problems/increasing-triplet-subsequence/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Create a `sequence` array to record increasing sequence.
- While iterate over `nums`, if the `num` in `nums` is smaller than elements of `sequence`, replace it.
- Keep the order of `sequence`.
- If `num` is greater than the last element in `sequence`, `nums` has an increasing triplet subsequence.
- You can increase a size of `sequence` to find `n-length subsequence` of `nums`.
- Runtime Complexity: **O(n)**

```typescript
function increasingTriplet(nums: number[]): boolean {
  const sequence = [Infinity, Infinity];
  for (const num of nums) {
    let index = sequence.length - 1;
    for (; index >= 0 && sequence[index] >= num; index--);
    if (index === sequence.length - 1) return true;
    sequence[index + 1] = num;
  }
  return false;
}
```

## Other's Solution

- Shorter solution but not scalable.
- Runtime Complexity: **O(n)**

```typescript
function increasingTriplet(nums: number[]): boolean {
  let [first, second] = [Infinity, Infinity];
  for (const num of nums) {
    if (num <= first) first = num;
    else if (num <= second) second = num;
    else return true;
  }
  return false;
}
```
