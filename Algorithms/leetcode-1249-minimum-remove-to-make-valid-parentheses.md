# [LeetCode] 1249. Minimum Remove to Make Valid Parentheses

## Problem

> Given a string s of `'('` , `')'` and lowercase English characters.
> Your task is to remove the minimum number of parentheses ( `'('` or `')'`, in any positions ) so that the resulting parentheses string is valid and return **any** valid string.
> Formally, a parentheses string is valid if and only if:
>
> - It is the empty string, contains only lowercase characters, or
> - It can be written as `AB` (`A` concatenated with `B`), where `A` and `B` are valid strings, or
> - It can be written as `(A)`, where `A` is a valid string.
>
> [[LeetCode] 1249. Minimum Remove to Make Valid Parentheses](https://leetcode.com/problems/minimum-remove-to-make-valid-parentheses/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Solved without using stack but basic thought is similar.
- Count left parentheses, iterating over `s`. `leftCount` is equal to the length of imaginary stack. Count up whenever meeting `'('`, count down whenever meeting '`)`'. However, If `')'` appears with no remaining `leftCount`, drop that parenthesis.
- Likewise, filter left parentheses iterate over `s` from the end to the beginning.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function minRemoveToMakeValid(s: string): string {
  return removeInvalidLeftParentheses(removeInvalidRightParentheses(s));
}

function removeInvalidRightParentheses(s: string): string {
  let leftCount = 0;
  let result = "";

  for (const letter of s) {
    if (!leftCount && letter === ")") continue;
    if (letter === "(") leftCount++;
    else if (letter === ")") leftCount--;
    result += letter;
  }

  return result;
}

function removeInvalidLeftParentheses(s: string): string {
  let rightCount = 0;
  let result = "";

  for (let i = s.length - 1; i >= 0; i--) {
    const letter = s[i];
    if (!rightCount && letter === "(") continue;
    if (letter === ")") rightCount++;
    else if (letter === "(") rightCount--;
    result = `${letter}${result}`;
  }

  return result;
}
```

## Other's Solution

- Surprisingly, my solution was similar to other up-voted solutions.
