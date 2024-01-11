# [[LeetCode] 1431. Kids With the Greatest Number of Candies](https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/description)

## Problem

> There are `n` kids with candies. You are given an integer array `candies`, where each `candies[i]` represents the number of candies the `ith` kid has, and an integer `extraCandies`, denoting the number of extra candies that you have.
>
> Return _a boolean array `result` of length `n`, where `result[i]` is `true` if, after giving the `ith` kid all the `extraCandies`, they will have the **greatest** number of candies among all the kids, or `false` otherwise_.
>
> Note that **multiple** kids can have the **greatest** number of candies.

## Solution

- Find the maximum candies, compare all elements with the sum of each candy and extraCandies.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function kidsWithCandies(candies: number[], extraCandies: number): boolean[] {
  const max = Math.max(...candies);
  return candies.map((candy) => candy + extraCandies >= max);
}
```
