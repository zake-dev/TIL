# [[LeetCode] 128. Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/description)

# Solution - TypeScript

```typescript
function longestConsecutive(nums: number[]): number {
  const set = new Set<number>();
  for (const num of nums) set.add(num);

  let max = 0;
  for (const num of set) {
    if (set.has(num - 1)) continue;

    let count = 1;
    let iter = num;
    while (set.has(iter + 1)) {
      count++;
      iter++;
    }
    max = Math.max(max, count);
  }

  return max;
}
```
