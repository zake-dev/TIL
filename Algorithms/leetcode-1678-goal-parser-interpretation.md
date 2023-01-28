# [LeetCode] 1678. Goal Parser Interpretation

## Problem

> You own a **Goal Parser** that can interpret a string `command`. The `command` consists of an alphabet of `"G"`, `"()"` and/or `"(al)"` in some order. The Goal Parser will interpret `"G"` as the string `"G"`, `"()"` as the string `"o"`, and `"(al)"` as the string `"al"`. The interpreted strings are then concatenated in the original order.
> Given the string `command`, return _the Goal Parser's interpretation of `command`_.
> [[LeetCode] 1678. Goal Parser Interpretation](https://leetcode.com/problems/goal-parser-interpretation/?envType=study-plan&id=programming-skills-i)

## Solution

- Naive way to solve.
- Used regex to replace target characters.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function interpret(command: string): string {
  const firstParsed = command.replace(/\(\)/g, "o");
  const secondParsed = firstParsed.replace(/\(al\)/g, "al");
  return secondParsed;
}
```

## Other's Solution

- You can also parse string with loops.
