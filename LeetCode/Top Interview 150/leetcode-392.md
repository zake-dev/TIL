# [[LeetCode] 392. Is Subsequence](https://leetcode.com/problems/is-subsequence/description)

# Solution - TypeScript

```typescript
function isSubsequence(s: string, t: string): boolean {
  let si = 0;
  let ti = 0;
  while (ti < t.length) {
    if (si >= s.length) return true;
    if (t[ti] === s[si]) si++;
    ti++;
  }
  return si >= s.length;
}
```
