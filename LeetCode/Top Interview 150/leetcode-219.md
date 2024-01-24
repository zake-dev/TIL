# [[LeetCode] 219. Contains Duplicate II](https://leetcode.com/problems/contains-duplicate-ii/description)

# Solution - TypeScript

```typescript
function containsNearbyDuplicate(nums: number[], k: number): boolean {
  const map = new Map<number, number>();
  for (let i = 0; i < nums.length; i++) {
    const distance = Math.abs(map.get(nums[i]) - i);
    if (distance <= k) return true;
    map.set(nums[i], i);
  }
  return false;
}
```
