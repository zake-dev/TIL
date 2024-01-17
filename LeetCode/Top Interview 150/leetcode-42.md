# [[LeetCode] 42. Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/description)

# Solution - TypeScript

```typescript
function trap(height: number[]): number {
  let trapped = 0;
  let [leftMax, rightMax] = [-Infinity, -Infinity];
  let [left, right] = [0, height.length - 1];
  while (left < right) {
    leftMax = Math.max(leftMax, height[left]);
    rightMax = Math.max(rightMax, height[right]);
    trapped +=
      leftMax < rightMax
        ? leftMax - height[left++]
        : rightMax - height[right--];
  }
  return trapped;
}
```
