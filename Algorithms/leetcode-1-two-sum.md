# [LeetCode] 1. Two Sum

## Problem

> Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.
> You may assume that each input would have **exactly one solution**, and you may not use the _same_ element twice.
> You can return the answer in any order.
> [[LeetCode] 1. Two Sum](https://leetcode.com/problems/two-sum/?envType=study-plan&id=data-structure-i)

## Solution

- Iterate over nums, memorize current index of the element in HashMap.
- If the `pair number` which is `target - current number` exists on the HashMap, return the current index and pair number index.
- Runtime Complexity: **O(n)**

```typescript
function twoSum(nums: number[], target: number): number[] {
  const hashMap = {};
  for (let i = 0; i < nums.length; i++) {
    let num = nums[i];
    let pairNum = target - num;
    if (pairNum in hashMap) return [i, hashMap[pairNum]];
    hashMap[num] = i;
  }
}
```

## Other's Solution

- It can also be solved by using `Brute-Force Algorithm` if the size of the input is small.
- Runtime Complexity: \*\*O(n^2)

```typescript
function twoSum(nums: number[], target: number): number[] {
  for (let i = 0; i < nums.length - 1; i++)
    for (let j = i + 1; j < nums.length; j++)
      if (nums[i] + nums[j] === target) return [i, j];
}
```
