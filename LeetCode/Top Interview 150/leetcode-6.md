# [[LeetCode] 6. Zigzag Coversion](https://leetcode.com/problems/zigzag-conversion/description)

# Solution - TypeScript

```typescript
function convert(s: string, numRows: number): string {
  const rows = Array.from(Array(numRows), () => "");

  for (let i = 0; i < s.length; ) {
    for (let j = 0; i < s.length && j < numRows; i++, j++) rows[j] += s[i];
    for (let k = numRows - 2; i < s.length && k > 0; i++, k--) rows[k] += s[i];
  }

  return rows.reduce((a, b) => a + b);
}
```
