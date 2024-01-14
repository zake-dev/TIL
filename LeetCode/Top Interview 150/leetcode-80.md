# [[LeetCode] 80. Remove Duplicates from Sorted Array II](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/description)

# Solution - TypeScript

```typescript
function removeDuplicates(nums: number[]): number {
  if (nums.length <= 2) return nums.length;

  let slow = 1;
  for (let fast = 2; fast < nums.length; fast++) {
    if (nums[fast] !== nums[slow - 1]) {
      nums[++slow] = nums[fast];
    }
  }

  return slow + 1;
}
```
