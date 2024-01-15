# [[LeetCode] 45. Jump Game II](https://leetcode.com/problems/jump-game-ii)

# Solution - TypeScript

```typescript
function jump(nums: number[]): number {
  for (let i = 1; i < nums.length; i++) {
    nums[i] = Math.max(nums[i] + i, nums[i - 1]);
  }

  let count = 0;
  for (let i = 0; i < nums.length - 1; i = nums[i]) count++;

  return count;
}
```
