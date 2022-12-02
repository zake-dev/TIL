# [LeetCode] 217. Contains Duplicate

## Problem

> Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.
> [[LeetCode] 217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/?envType=study-plan&id=data-structure-i)

## Solution

- Iterate over given nums, add its elements to HashSet.
- If the elements already added in HashSet, return true.
- If Every elements is unique, return false.
- Runtime Complexity: **O(n)**

```typescript
function containsDuplicate(nums: number[]): boolean {
  const hashSet = new Set();
  for (const num of nums) {
    if (hashSet.has(num)) return true;
    hashSet.add(num);
  }
  return false;
}
```

## Other's Solution

- Sort the given array.
- If continuos numbers in array are same, the array has duplicate values.
- Runtime Complexity: **O(n\*logn)**

```typescript
function containsDuplicate(nums: number[]): boolean {
  nums.sort((a, b) => a - b);
  for (let i = 0; i < nums.length - 1; i++)
    if (nums[i] === nums[i + 1]) return true;
  return false;
}
```
