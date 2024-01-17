# [[LeetCode] 58. Length of Last Word](https://leetcode.com/problems/length-of-last-word/description)

# Solution - TypeScript

```typescript
function lengthOfLastWord(s: string): number {
  s = s.trim();
  let length = 0;
  for (let i = s.length - 1; i >= 0; i--) {
    if (s[i] === " ") return length;
    length++;
  }
  return length;
}
```
