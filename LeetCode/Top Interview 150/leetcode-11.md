# [[LeetCode] 11. Contiainer With Most Water](https://leetcode.com/problems/container-with-most-water/description)

# Solution - TypeScript

```typescript
function maxArea(heights: number[]): number {
  let left = 0;
  let right = heights.length - 1;
  let max = 0;
  while (left < right) {
    const width = right - left;
    const height = Math.min(heights[left], heights[right]);
    max = Math.max(max, width * height);
    if (heights[left] < heights[right]) left++;
    else right--;
  }
  return max;
}
```
