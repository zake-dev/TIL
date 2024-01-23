# [[LeetCode] 290. Word Pattern](https://leetcode.com/problems/word-pattern/description)

# Solution - TypeScript

```typescript
function wordPattern(pattern: string, s: string): boolean {
  const words = s.split(" ");
  if (pattern.length !== words.length) return false;

  const pMap = new Map<string, string>();
  const wMap = new Map<string, string>();

  for (let i = 0; i < pattern.length; i++) {
    const isRecorded = pMap.has(pattern[i]) || wMap.has(words[i]);
    const isMatching =
      pMap.get(pattern[i]) === words[i] && wMap.get(words[i]) === pattern[i];
    if (isRecorded && !isMatching) return false;
    pMap.set(pattern[i], words[i]);
    wMap.set(words[i], pattern[i]);
  }

  return true;
}
```
