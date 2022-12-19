# [LeetCode] 560. Subarray Sum Equals K

## Problem

> Given an array of integers `nums` and an integer `k`, return _the total number of subarrays whose sum equals to `k`_.
> A subarray is a contiguous non-empty sequence of elements within an array.
> [[LeetCode] 560. Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Map `nums` array to _cumulative sum array_. Each elements `a[i]` in _cumulative sum array_ represents the sum of `nums[0]` to `nums[i]`.
- If mapped element `n[i]` is equal to `k` increase the `count`.
- Also, count the prefix sum of `nums` array if `num` of `nums` were in the hash map.
- Hash map will store how many times the `num + k` is appeared which is a pair for prefix sum.
- Runtime Complexity: **O(n)**

```typescript
function subarraySum(nums: number[], k: number): number {
  for (let i = 1; i < nums.length; i++) nums[i] += nums[i - 1];

  const hashMap = new Map<number, number>();
  let count = 0;
  for (const num of nums) {
    if (num === k) count++;
    if (hashMap.has(num)) count += hashMap.get(num);
    hashMap.set(num + k, (hashMap.get(num + k) ?? 0) + 1);
  }

  return count;
}
```

## Other's Solution

- My solution has a best runtime complexity than others. All up-voted solutions were similar to mine.
