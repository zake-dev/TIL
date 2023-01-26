# [LeetCode] 283. Move Zeroes

## Problem

> Given an integer array `nums`, move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.
> **Note** that you must do this in-place without making a copy of the array.
> [[LeetCode] 283. Move Zeroes](https://leetcode.com/problems/move-zeroes/description/?envType=study-plan&id=programming-skills-i)

## Solution

- Iterate over `nums`, swap `0` with next non-zero elements whenever it appears.
- It will push `0`s to the right side of an array.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function moveZeroes(nums: number[]): void {
  for (let i = 0; i < nums.length; i++) {
    if (nums[i] === 0) {
      const next = findIndexOfNextNonZero(nums, i);
      if (next === -1) break;
      [nums[i], nums[next]] = [nums[next], nums[i]];
    }
  }
}

function findIndexOfNextNonZero(nums: number[], index: number): number {
  for (let i = index; i < nums.length; i++) if (nums[i] !== 0) return i;
  return -1;
}
```

## Other's Solution

- Same approach applied for others as well.
