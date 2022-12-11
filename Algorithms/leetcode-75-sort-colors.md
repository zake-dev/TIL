# [LeetCode] 75. Sort Colors

## Problem

> Given an array `nums` with `n` objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.
> We will use the integers `0`, `1`, and `2` to represent the color red, white, and blue, respectively.
> You must solve this problem without using the library's sort function.
> [[LeetCode] 75. Sort Colors](https://leetcode.com/problems/sort-colors/description/?envType=study-plan&id=data-structure-ii)

## Solution

- `nums` only contain `0`, `1`, or `2` _3 types_. We can count and fill the `nums` using constant space with **O(n + m)** speed.
- Runtime Complexity: **O(n)**

```typescript
/**
 Do not return anything, modify nums in-place instead.
 */
function sortColors(nums: number[]): void {
  let redCount = 0;
  let whiteCount = 0;
  let blueCount = 0;
  for (const num of nums) {
    if (num === 0) redCount++;
    else if (nums === 1) redCount++;
    else blueCount++;
  }

  let index = 0;
  while (redCount--) nums[index++] = 0;
  while (whiteCount--) nums[index++] = 1;
  while (blueCount--) nums[index++] = 2;
}
```

## Other's Solution

- Using two pointers from the first and the last.
- Swap `0` to left, Swap `2` to right.
- Runtime Complexity: **O(n)**

```typescript
function sortColors(nums: number[]): void {
  let first = 0;
  let last = nums.length - 1;
  for (let i = 0; i <= last; i++) {
    if (nums[i] === 0) {
      [nums[first], nums[i]] = [nums[i], nums[first]];
      first++;
    } else if (nums[i] === 2) {
      [nums[last], nums[i]] = [nums[i], nums[last]];
      i--;
      last--;
    }
  }
}
```
