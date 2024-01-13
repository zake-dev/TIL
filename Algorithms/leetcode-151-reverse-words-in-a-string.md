# [[LeetCode] 151. Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/description)

## Problem

> Given an input string `s`, reverse the order of the **words**.
>
> A **word** is defined as a sequence of non-space characters. The **words** in `s` will be separated by at least one space.
>
> Return _a string of the words in reverse order concatenated by a single space_.
>
> Note that `s` may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.

## Solution

- Trim the given `s` first.
- By using RegExp, split `s` into `words`.
- Reverse it and join with a single space.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function reverseWords(s: string): string {
  const words = s.trim().split(/ +/);
  return words.reverse().join(" ");
}
```
