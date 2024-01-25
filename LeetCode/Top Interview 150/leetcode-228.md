# [[LeetCode] 228. Summary Ranges](https://leetcode.com/problems/summary-ranges/description)

# Solution - TypeScript

```typescript
function summaryRanges(nums: number[]): string[] {
  if (nums.length === 0) return [];

  const ranges: string[] = [];

  let start = nums[0];
  let end = nums[0];
  for (let i = 1; i < nums.length; i++) {
    const num = nums[i];
    if (end + 1 === num) {
      end = num;
      continue;
    }

    const range = start === end ? start.toString() : `${start}->${end}`;
    ranges.push(range);
    start = num;
    end = num;
  }
  const range = start === end ? start.toString() : `${start}->${end}`;
  ranges.push(range);

  return ranges;
}
```
