# [LeetCode] 20. Valid Parentheses

## Problem

> Given a string s containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

> An input string is valid if:
>
> - Open brackets must be closed by the same type of brackets.
> - Open brackets must be closed in the correct order.
> - Every close bracket has a corresponding open bracket of the same type.

> [[LeetCode] 1. Two Sum](https://leetcode.com/problems/two-sum/?envType=study-plan&id=data-structure-i)

## Solution

- Use `stack` to check the `last bracket` can be pair of the `current bracket`.
- If `bracket` is one of `opening brackets`, push it to the `stack`.
- If `stack` is not empty, but the `last bracket` is not a pair of `current bracket`, return `false`.
- Otherwise, pop `last bracket` from the `stack`.
- Runtime Complexity: **O(n)**

```typescript
const zip = (a: any[], b: any[]) => a.map((k, i) => [k, b[i]]);

function isValid(s: string): boolean {
  const OPENING_BRACKETS = ["(", "{", "["];
  const CLOSING_BRACKETS = [")", "}", "]"];
  const VALID_PAIRS = Object.fromEntries(
    zip(CLOSING_BRACKETS, OPENING_BRACKETS)
  );

  const stack = [];
  for (const bracket of s) {
    if (OPENING_BRACKETS.includes(bracket)) {
      stack.push(bracket);
      continue;
    }
    if (stack[stack.length - 1] !== VALID_PAIRS[bracket]) return false;
    stack.pop();
  }
  return stack.length === 0;
}
```

## Other's Solution

- No other brilliant solutions.
