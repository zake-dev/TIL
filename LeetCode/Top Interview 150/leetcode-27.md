# [[LeetCode] 27. Remove Element](https://leetcode.com/problems/remove-element/description)

# Solution - TypeScript

```typescript
function removeElement(nums: number[], val: number): number {
  let left = 0;
  for (let i = 0; i < nums.length; i++) {
    if (nums[i] === val) continue;
    nums[left++] = nums[i];
  }
  return left;
}
```
