# [LeetCode] 125. Valid Palindrome

## Problem

> A phrase is a **palindrome** if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.
> Given a string `s`, return _`true` if it is a palindrome, or `false` otherwise_.
> [[LeetCode] 125. Valid Palindrome](https://leetcode.com/problems/valid-palindrome/description/)

## Solution

- Filter non-alphanumeric characters in the given string `s` and parse it into lowercase.
- Check if it is a palindrome.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function isPalindrome(s: string): boolean {
  const parsed = removeNonAlphanumeric(s).toLowerCase();
  for (
    let [left, right] = [0, parsed.length - 1];
    left < right;
    left++, right--
  )
    if (parsed[left] !== parsed[right]) return false;
  return true;
}

function removeNonAlphanumeric(s: string): string {
  return s.replace(/[^0-9a-zA-Z]/g, "");
}
```

## Other's Solution

- Most solutions are similar to mine.
