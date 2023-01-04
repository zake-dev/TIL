# [LeetCode] 66. Plus One

## Problem

> You are given a **large integer** represented as an integer array `digits`, where each `digits[i]` is the `ith` digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading `0`'s.
> Increment the large integer by one and return _the resulting array of digits_.
> [[LeetCode] 66. Plus One](https://leetcode.com/problems/plus-one/description/)

## Solution

- From end to start of index in `digits`, increase `1`. If there is a `carry`, keep added up next digit.
- Return `digits` immediately if there is no `carry`.
- Place `1` in front of the `digits` if the for-loop completely passes.
- Time Complexity: **O(n)**, Space Complexity: **O(1) on average**, **O(n) at worst**

```typescript
function plusOne(digits: number[]): number[] {
  for (let i = digits.length - 1; i >= 0; i--) {
    if (digits[i] < 9) {
      digits[i]++;
      return digits;
    }
    digits[i] = 0;
  }
  return [1, ...digits];
}
```

## Other's Solution

- This is a simple implementation problem.
