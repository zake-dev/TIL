# [[LeetCode] 169. Majority Element](https://leetcode.com/problems/majority-element/description)

# Solution - TypeScript

```typescript
function majorityElement(nums: number[]): number {
  let majority = nums[0];
  let count = 0;
  for (let i = 0; i < nums.length; i++) {
    if (count === 0) majority = nums[i];
    count += majority === nums[i] ? 1 : -1;
  }
  return majority;
}
```
