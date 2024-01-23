# [[LeetCode] 242. Valid Anagram](https://leetcode.com/problems/valid-anagram)

# Solution - TypeScript

```typescript
function isAnagram(s: string, t: string): boolean {
  if (s.length !== t.length) return false;

  const counter = new Map<string, number>();
  for (const ch of s) {
    if (!counter.has(ch)) counter.set(ch, 0);
    counter.set(ch, counter.get(ch) + 1);
  }
  for (const ch of t) {
    const count = counter.get(ch);
    if (isNaN(count) || count <= 0) return false;
    counter.set(ch, count - 1);
  }
  return true;
}
```
