# [[LeetCode] 209. Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/description)

# Solution - TypeScript

```typescript
function minSubArrayLen(target: number, nums: number[]): number {
  let minLength = Infinity;
  let left = 0;
  let right = 0;
  let sum = 0;
  while (left <= right && left < nums.length) {
    while (right < nums.length && sum < target) {
      sum += nums[right++];
    }
    if (sum >= target) minLength = Math.min(minLength, right - left);
    sum -= nums[left];
    left++;
  }

  return minLength === Infinity ? 0 : minLength;
}
```
