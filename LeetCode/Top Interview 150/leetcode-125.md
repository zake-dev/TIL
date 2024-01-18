# [[LeetCode] 125. Valid Palindrome](https://leetcode.com/problems/valid-palindrome/description)

# Solution - TypeScript

```typescript
function isPalindrome(s: string): boolean {
  const refined = s.replaceAll(/[^A-Z^a-z0-9]/g, "").toLowerCase();
  for (let i = 0; i < refined.length / 2; i++) {
    if (refined[i] !== refined[refined.length - 1 - i]) return false;
  }
  return true;
}
```
