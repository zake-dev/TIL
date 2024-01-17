# [[LeetCode] 14. Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/description)

# Solution - TypeScript

```typescript
function longestCommonPrefix(strs: string[]): string {
  let commonPrefix = strs[0];
  for (let i = 1; i < strs.length; i++) {
    if (commonPrefix === "") return "";
    for (let j = 0; j < commonPrefix.length; j++) {
      if (strs[i][j] !== commonPrefix[j])
        commonPrefix = commonPrefix.substring(0, j);
    }
  }
  return commonPrefix;
}
```
