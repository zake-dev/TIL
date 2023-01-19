# [LeetCode] 215. Kth Largest Element in Array

## Problem

> Given an integer array `nums` and an integer `k`, return the `kth` largest element in the array.
> Note that it is the `kth` largest element in the sorted order, not the `kth` distinct element.
> You must solve it in `O(n)` time complexity.
> [[LeetCode] 215. Kth Largest Element in Array](https://leetcode.com/problems/kth-largest-element-in-an-array/description/)

## Solution

- Failed to solve in `O(n)` time complexity.
- Easiest way to solve over `O(n)` time complexity is sorting and return `k - 1` indexed element.
- Time Complexity: **O(n\*logn)**, Space Complexity: **O(1)**

```typescript
function findKthLargest(nums: number[], k: number): number {
  nums.sort((a, b) => b - a);
  return nums[k - 1];
}
```

## Other's Solution

- Proper solution is using quick select algorithm. This algorithm find `nth` smallest/largest number in unsorted array in `O(n)` time complexity in average. Only the worst case takes `O(n^2)` but it appears rarely.
- By partitioning elements with `pivot`, leave left or right side of array to find.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function findKthLargest(nums: number[], k: number): number {
  const n: number = nums.length;
  return quickSelect(nums, n - k, 0, n - 1);
}

function quickSelect(
  nums: number[],
  targetIndex: number,
  start: number,
  end: number
): number {
  if (start === end) return nums[start];

  let random: number = getRandom(start, end);
  let pivot: number = partition(nums, random, start, end);

  if (pivot > targetIndex) {
    return quickSelect(nums, targetIndex, start, pivot - 1);
  } else if (pivot < targetIndex) {
    return quickSelect(nums, targetIndex, pivot + 1, end);
  } else {
    return nums[pivot];
  }
}

function partition(
  nums: number[],
  random: number,
  start: number,
  end: number
): number {
  let pivot: number = nums[random];
  swap(nums, start, random);
  let pivotIndex: number = start;

  for (let i = start + 1; i <= end; i++) {
    if (nums[i] < pivot) {
      pivotIndex++;
      swap(nums, i, pivotIndex);
    }
  }

  swap(nums, start, pivotIndex);
  return pivotIndex;
}

function swap(nums: number[], index1: number, index2: number): void {
  [nums[index1], nums[index2]] = [nums[index2], nums[index1]];
}

function getRandom(start: number, end: number): number {
  return start + Math.floor((end - start) / 2);
}
```
