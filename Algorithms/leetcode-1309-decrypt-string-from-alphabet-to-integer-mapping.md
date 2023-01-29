# [LeetCode] 1309. Decrypt String from Alphabet to Integer Mapping

## Problem

> You are given a string `s` formed by digits and `'#'`. We want to map `s` to English lowercase characters as follows:
>
> - Characters (`'a'` to `'i'`) are represented by (`'1'` to `'9'`) respectively.
> - Characters (`'j'` to `'z'`) are represented by (`'10#'` to `'26#'`) respectively.
>
> Return _the string formed after mapping_.
> The test cases are generated so that a unique mapping will always exist.
> [[LeetCode] 1309. Decrypt String from Alphabet to Integer Mapping](https://leetcode.com/problems/decrypt-string-from-alphabet-to-integer-mapping/description/?envType=study-plan&id=programming-skills-i)

## Solution

- While iterating over `s`, check current number represents a single character or it is a set of 3-length number like `'10#'`.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function freqAlphabets(s: string): string {
  const pattern = "#abcdefghijklmnopqrstuvwxyz";
  let decrypted = "";
  for (let i = 0; i < s.length; i++) {
    if (s[i + 2] === "#") {
      const index = +s.slice(i, i + 2);
      decrypted += pattern[index];
      i += 2;
      continue;
    }

    decrypted += pattern[+s[i]];
  }
  return decrypted;
}
```

## Other's Solution

- This is a simple implementation problem.
