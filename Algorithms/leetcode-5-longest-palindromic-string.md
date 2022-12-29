# [LeetCode] 5. Longest Palindromic String

## Problem

> Given a string `s`, return _the longest palindromic substring in `s`_.
> [[LeetCode] 5. Longest Palindromic String](https://leetcode.com/problems/longest-palindromic-substring/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Brute-Force approach. Iterate over all substrings, check if the substring is palindrome.
- If so, compare with current longest palindrome substring.
- Skip the range less than the length of current longest palindrome substring.
- Time Complexity: **O(n^3)** Space Complexity: **O(1)**

```typescript
function longestPalindrome(s: string): string {
  let longest = "";
  for (let i = 0; i < s.length; i++) {
    for (let j = s.length - 1; j >= 0; j--) {
      if (j - i < longest.length) break;

      const substring = s.slice(i, j + 1);
      if (isPalindrome(substring)) longest = substring;
    }
  }
  return longest;
}

function isPalindrome(text: string): boolean {
  const length = text.length;
  for (let i = 0; i < length / 2; i++)
    if (text[i] !== text[length - i - 1]) return false;
  return true;
}
```

## Other's Solution

- This solution directly check if the substring is palindrome or not in first for-loop.
- Basic thought of this solution is there are two types of palindrome exist which has odd-length and even-length.
- From the middle of the palindrome substring, check next characters on the border of current substring. For example, `'a' -> 'bab' -> 'cbab'` or `'aa' -> 'baab' -> 'cbaabc'`.
- `start` and `end` indicates the indices of the longest palindrome substring.
- Whenever every palindromic substring found, update `start` and `end` positions.
- `j` is a simple trick to check odd-length substring and even-length substring.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function longestPalindrome(s: string): string {
  let [start, end] = [0, 0];

  for (let i = 0; i < s.length; i++)
    for (const j of [i, i + 1])
      for (
        let [left, right] = [i, j];
        s[left] && s[left] === s[right];
        left--, right++
      )
        if (right - left > end - start) [start, end] = [left, right];

  return s.substring(start, end + 1);
}
```
