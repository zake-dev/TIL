# [[LeetCode] 605. Can Place Flowers](https://leetcode.com/problems/can-place-flowers/description)

## Problem

> You have a long flowerbed in which some of the plots are planted, and some are not. However, flowers cannot be planted in **adjacent** plots.
>
> Given an integer array `flowerbed` containing `0`'s and `1`'s, where `0` means empty and `1` means not empty, and an integer `n`, return `true` _if `n` new flowers can be planted in the `flowerbed` without violating the no-adjacent-flowers rule and `false` otherwise_.

## Solution

- Manually plant extra floweres during loop. Count it.
- This can be optimized by early returning inside for-loop. But I think this is more readable.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function canPlaceFlowers(flowerbed: number[], n: number): boolean {
  let remainingPlots = 0;
  for (let i = 0; i < flowerbed.length; i++) {
    if (flowerbed[i] === 1) continue;
    if (i > 0 && flowerbed[i - 1] === 1) continue;
    if (i < flowerbed.length - 1 && flowerbed[i + 1] === 1) continue;
    flowerbed[i] = 1;
    remainingPlots++;
  }
  return remainingPlots >= n;
}
```
