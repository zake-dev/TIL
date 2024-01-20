# [[LeetCode] 3. Longest Substring Without Repeating characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/description)

# Solution - TypeScript

```typescript
function lengthOfLongestSubstring(s: string): number {
  let maxLength = 0;
  let left = 0;
  let right = 0;
  const set = new Set<string>();
  while (right < s.length) {
    while (set.has(s[right])) {
      set.delete(s[left]);
      left++;
    }
    set.add(s[right]);
    maxLength = Math.max(maxLength, set.size);
    right++;
  }
  return maxLength;
}
```
