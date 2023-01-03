# [LeetCode] 26. Remove Duplicates from Sorted Array

## Problem

> Given an integer array `nums` sorted in **non-decreasing order**, remove the duplicates in-place such that each unique element appears only **once**. The **relative order** of the elements should be kept the **same**.
> Since it is impossible to change the length of the array in some languages, you must instead have the result be placed in the **first part** of the array `nums`. More formally, if there are `k` elements after removing the duplicates, then the first `k` elements of `nums` should hold the final result. It does not matter what you leave beyond the first `k` elements.
> Return _`k` after placing the final result in the first `k` slots of `nums_`.
> Do **not** allocate extra space for another array. You must do this by **modifying the input array** in-place with O(1) extra memory.
> [[LeetCode] 26. Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)

## Solution

- Use two pointers one of which iterates over whole array, but the other points only for the filtered array.
- Memorize `previous` value of array, if current value is equal to `previous`, skip.
- Overwrite the value on `filteredIndex` by `index` which is a very next unique number.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function removeDuplicates(nums: number[]): number {
  let previous = NaN;
  let duplicateCount = 0;
  for (
    let [index, filteredIndex] = [0, 0];
    index < nums.length;
    index++, filteredIndex++
  ) {
    while (nums[index] === previous) {
      duplicateCount++;
      index++;
    }
    nums[filteredIndex] = nums[index];
    previous = nums[filteredIndex];
  }
  return nums.length - duplicateCount;
}
```

## Other's Solution

- Same logic but more elegant way to implement.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function removeDuplicates(nums: number[]): number {
  let tailIndex = 0;
  for (let i = 1; i < nums.length; i++)
    if (nums[i] !== nums[tailIndex]) {
      tailIndex++;
      nums[tailIndex] = nums[i];
    }
  return tailIndex + 1;
}
```
