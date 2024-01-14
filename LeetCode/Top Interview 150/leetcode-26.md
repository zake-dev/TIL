# [[LeetCode] 26. Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description)

# Solution - TypeScript

```typescript
function removeDuplicates(nums: number[]): number {
  let slow = 0;
  for (let fast = 0; fast < nums.length; fast++) {
    if (nums[slow] !== nums[fast]) nums[++slow] = nums[fast];
  }
  return slow + 1;
}
```
