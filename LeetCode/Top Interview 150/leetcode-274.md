# [[LeetCode] 274. H-Index](https://leetcode.com/problems/h-index/description)

# Solution - TypeScript

```typescript
function hIndex(citations: number[]): number {
  citations.sort((a, b) => b - a);

  let h = 0;
  for (let i = 0; i < citations.length; i++) if (citations[i] > h) h++;
  return h;
}
```
