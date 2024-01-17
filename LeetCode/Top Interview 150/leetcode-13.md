# [[LeetCode] 13. Roman to Integer](https://leetcode.com/problems/roman-to-integer/description)

# Solution - TypeScript

```typescript
function romanToInt(s: string): number {
  const romanMap = {
    I: 1,
    V: 5,
    X: 10,
    L: 50,
    C: 100,
    D: 500,
    M: 1000,
  };
  let currentBase = 1;
  let sum = 0;
  for (let i = s.length - 1; i >= 0; i--) {
    const digit = romanMap[s[i]];
    sum = currentBase > digit ? sum - digit : sum + digit;
    currentBase = currentBase > digit ? currentBase : digit;
  }
  return sum;
}
```
