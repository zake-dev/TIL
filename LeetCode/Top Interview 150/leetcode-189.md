# [[LeetCode] 189. Rotate Array](https://leetcode.com/problems/rotate-array/description)

# Solution - TypeScript

```typescript
function reverse(nums: number[], start: number, end: number): void {
  while (start < end) {
    [nums[start], nums[end]] = [nums[end], nums[start]];
    start++;
    end--;
  }
}

function rotate(nums: number[], k: number): void {
  k = nums.length - (k % nums.length);
  reverse(nums, 0, k - 1);
  reverse(nums, k, nums.length - 1);
  reverse(nums, 0, nums.length - 1);
}
```
