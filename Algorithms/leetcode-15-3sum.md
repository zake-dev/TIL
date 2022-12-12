# [LeetCode] 15. 3Sum

## Problem

> Given an integer array `nums`, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.
> Notice that the solution set must not contain duplicate triplets.
> [[LeetCode] 15. 3Sum](https://leetcode.com/problems/3sum/?envType=study-plan&id=data-structure-ii)

## Solution

- Use two extra pointers over iteration.
- Firstly, sort the given `nums`.
- `j` is the left most pointer between `i` and _end of the array_, `k` is the right most pointer between `i` and _end of the array_.
- We will find that \_sum of `[nums[i], nums[j], nums[k]]` is equal to `0`. Push it into the `result`.
- We don't need duplicate triplets, so skip all the duplicates. Move pointers.
- Runtime Complexity: **O(n\*logn) + O(n^2) = O(n^2)**

```typescript
function threeSum(nums: number[]): number[][] {
  nums.sort((a, b) => a - b);
  const result: number[][] = [];

  let i = 0;
  while (i < nums.length - 2) {
    let j = i + 1;
    let k = nums.length - 1;

    while (j < k) {
      const sum = nums[i] + nums[j] + nums[k];
      if (sum < 0) j = skipDuplicates(nums, j);
      else if (sum > 0) k = skipDuplicates(nums, k, true);
      else {
        result.push([nums[i], nums[j], nums[k]]);
        j = skipDuplicates(nums, j);
        k = skipDuplicates(nums, k, true);
      }
    }

    i = skipDuplicates(nums, i);
  }

  return result;
}

function skipDuplicates(
  nums: number[],
  index: number,
  reverse: boolean = false
): number {
  if (reverse) while (nums[--index] === nums[index + 1]);
  else while (nums[++index] === nums[index - 1]);
  return index;
}
```

## Other's Solution

- It can be solved by using hash set as well, but this will cause TLE(Time Limit Exceeded) as it takes **O(n^2logn)**.
