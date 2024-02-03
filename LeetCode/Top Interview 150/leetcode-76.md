# [[LeetCode] 76. Minimum window Substring](https://leetcode.com/problems/minimum-window-substring/description)

# Solution - TypeScript

```typescript
function minWindow(s: string, t: string): string {
  const needCounter = new Map<string, number>();
  const haveCounter = new Map<string, number>();

  for (const c of t) {
    needCounter.set(c, (needCounter.get(c) ?? 0) + 1);
    haveCounter.set(c, 0);
  }

  let result = "";
  const totalNeed = needCounter.size;
  let totalHave = 0;
  for (let [left, right] = [0, 0]; right < s.length; right++) {
    const sr = s[right];
    if (needCounter.has(sr)) {
      haveCounter.set(sr, haveCounter.get(sr) + 1);
      if (needCounter.get(sr) === haveCounter.get(sr)) totalHave++;
    }

    for (; totalHave === totalNeed && left < s.length; left++) {
      if (result.length === 0 || right - left + 1 < result.length)
        result = s.substring(left, right + 1);

      const sl = s[left];
      if (needCounter.has(sl)) {
        haveCounter.set(sl, haveCounter.get(sl) - 1);
        if (needCounter.get(sl) > haveCounter.get(sl)) totalHave--;
      }
    }
  }

  return result;
}
```
