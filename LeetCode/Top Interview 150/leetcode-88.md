# [[LeetCode] 88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/description)

# Solution - TypeScript

```typescript
function merge(nums1: number[], m: number, nums2: number[], n: number): void {
  let right = m + n - 1;
  m--, n--;
  while (right >= 0 && n >= 0) {
    if (nums1[m] >= nums2[n]) nums1[right--] = nums1[m--];
    else nums1[right--] = nums2[n--];
  }
}
```
