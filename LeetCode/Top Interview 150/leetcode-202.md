# [[LeetCode] 202. Happy Number](https://leetcode.com/problems/happy-number)

# Solution - TypeScript

```typescript
function toHappy(n: number): number {
  let sum = 0;
  while (n > 0) {
    sum += Math.pow(n % 10, 2);
    n = Math.floor(n / 10);
  }
  return sum;
}

function isHappy(n: number): boolean {
  const visited = new Set<number>();
  while (n !== 1) {
    if (visited.has(n)) return false;
    visited.add(n);
    n = toHappy(n);
  }
  return true;
}
```
