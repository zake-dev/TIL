# [[LeetCode] 55. Jump Game](https://leetcode.com/problems/jump-game/description)

# Solution - TypeScript

```typescript
function canJump(nums: number[]): boolean {
  let canReach = nums.length - 1;
  for (let right = nums.length - 2; right >= 0; right--) {
    if (right + nums[right] >= canReach) canReach = right;
  }
  return canReach === 0;
}
```
