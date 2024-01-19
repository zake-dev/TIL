# [[LeetCode] 167. Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description)

# Solution - TypeScript

```typescript
function twoSum(numbers: number[], target: number): number[] {
  const map = new Map<number, number>();
  for (let i = 0; i < numbers.length; i++) {
    if (map.has(numbers[i])) return [map.get(numbers[i]) + 1, i + 1];
    map.set(target - numbers[i], i);
  }
}
```
