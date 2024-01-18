# [[LeetCode] 151. Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/description)

# Solution - TypeScript

```typescript
function reverseWords(s: string): string {
  return s.trim().split(/ +/g).reverse().join(" ");
}
```
