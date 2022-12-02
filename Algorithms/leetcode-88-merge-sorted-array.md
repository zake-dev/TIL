# [LeetCode] 88. Merge Sorted Array

## Problem

> You are given two integer arrays `nums1` and `nums2`, sorted in **non-decreasing order**, and two integers `m` and `n`, representing the number of elements in `nums1` and `nums2` respectively.
> **Merge** `nums1` and `nums2` into a single array sorted in **non-decreasing order**.
> The final sorted array should not be returned by the function, but instead be stored inside the array `nums1`. To accommodate this, `nums1` has a length of `m + n`, where the first `m` elements denote the elements that should be merged, and the last `n` elements are set to `0` and should be ignored. `nums2` has a length of `n`.
> [[LeetCode] 88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/?envType=study-plan&id=data-structure-i)

## Solution

- I know there is an algorithm takes **O(n)**, but I will use **O(n\*logn)** solution. It's a bit slow but is more readable and easy to write. If the size of the input was dramatically huge, I would use O(n) algorithm instead.
- Fill end of the `nums1` with `nums2`
- Sort `nums1`
- Runtime Complexity: **O(n\*logn)**

```typescript
function merge(nums1: number[], m: number, nums2: number[], n: number): void {
  for (let i = m; i < m + n; i++) nums1[i] = nums2[i - m];
  nums1.sort((a, b) => a - b);
}
```

## Other's Solution

- Brilliant solution that takes just **O(n)** runtime complexity with **O(1)** space complexity.
- Fill `nums1` from its back.
- Use 2 additional pointers `a` and `b` to follow the last remaining element of `nums1` and `nums2`.

```typescript
function merge(nums1: number[], m: number, nums2: number[], n: number): void {
  for (let i = m + n - 1, a = m - 1, b = n - 1; b >= 0; i--) {
    if (a >= 0 && nums1[a] > nums2[b]) nums1[i] = nums1[a--];
    else nums1[i] = nums2[b--];
  }
}
```
