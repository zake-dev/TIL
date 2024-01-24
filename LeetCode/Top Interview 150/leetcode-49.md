# [[LeetCode] 49. Group Anagrams](https://leetcode.com/problems/group-anagrams/description)

# Solution - TypeScript

```typescript
function groupAnagrams(strs: string[]): string[][] {
  const groups = new Map<string, string[]>();
  for (const str of strs) {
    const sorted = str.split("").sort().join("");
    if (!groups.has(sorted)) groups.set(sorted, []);
    groups.get(sorted).push(str);
  }
  return [...groups.values()];
}
```
