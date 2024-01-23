# [[LeetCode] 205. Isomorphic Stirngs](https://leetcode.com/problems/isomorphic-strings/description)

# Solution - TypeScript

```typescript
function isIsomorphic(s: string, t: string): boolean {
  const sMap = new Map<string, string>();
  const tMap = new Map<string, string>();
  for (let i = 0; i < s.length; i++) {
    const isRecorded = sMap.has(s[i]) || tMap.has(t[i]);
    const isMatching = sMap.get(s[i]) === t[i] && tMap.get(t[i]) === s[i];
    if (isRecorded && !isMatching) return false;
    sMap.set(s[i], t[i]);
    tMap.set(t[i], s[i]);
  }
  return true;
}
```
