# [[LeetCode] 383. Ransom Note](https://leetcode.com/problems/ransom-note/description)

# Solution - TypeScript

```typescript
function canConstruct(ransomNote: string, magazine: string): boolean {
  const counter = new Map<string, number>();
  for (const ch of magazine) {
    if (!counter.has(ch)) counter.set(ch, 0);
    counter.set(ch, counter.get(ch) + 1);
  }
  for (const ch of ransomNote) {
    const count = counter.get(ch);
    if (isNaN(count) || count <= 0) return false;
    counter.set(ch, count - 1);
  }
  return true;
}
```
