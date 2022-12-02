# [LeetCode] 350. Intersection of Two Arrays II

## Problem

> Given two integer arrays `nums1` and `nums2`, return _an array of their intersection_. Each element in the result must appear as many times as it shows in both arrays and you may return the result in **any order**.
> [[LeetCode] 350. Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii/)

## Solution

- Sort two arrays first.
- Use two pointers `a` and `b` to track `nums1` and `nums2`.
- Add a number when `nums1[a]` and `nums2[b]` is same.
- Otherwise, move the pointer forward which indicates smaller number. For example, `nums1[a]` is smaller than `nums[b]`, move the pointer `a`.
- Runtime Complexity: **O(n\*logn)**

```typescript
function intersect(nums1: number[], nums2: number[]): number[] {
  const intersection = [];
  nums1.sort((a, b) => a - b);
  nums2.sort((a, b) => a - b);
  for (let a = 0, b = 0; a < nums1.length && b < nums2.length; a++, b++) {
    if (nums1[a] < nums2[b]) b--;
    else if (nums1[a] > nums2[b]) a--;
    else intersection.push(nums1[a]);
  }
  return intersection;
}
```

## Other's Solution

- Use empty arrays as frequency maps. This solution will only work when the constraints are reasonably small.
- Count the frequencies of `num` appears in `nums1` and `nums2`.
- Take a minimum value between two frequencies.
- Add `num` to `result` as much sa it appears in both.
- Runtime Complexity: **O(n)**

```typescript
function intersect(nums1: number[], nums2: number[]): number[] {
  const freq1 = new Array(1001).fill(0);
  const freq2 = new Array(1001).fill(0);
  for (const num of nums1) freq1[num]++;
  for (const num of nums2) freq2[num]++;

  const intersection = new Array(1001).fill(0);
  for (let i = 0; i < 1001; i++) intersection[i] = Math.min(freq1[i], freq2[i]);

  const result = [];
  for (let i = 0; i < 1001; i++) {
    while (intersection[i] !== 0) {
      result.push(i);
      intersection[i]--;
    }
  }
  return result;
}
```
