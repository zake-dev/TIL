# [[LeetCode] 20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description)

# Solution - TypeScript

```typescript
function isValid(s: string): boolean {
  const stack: string[] = [];
  for (const c of s) {
    switch (c) {
      case "(":
      case "{":
      case "[":
        stack.push(c);
        break;
      case ")":
        if (stack[stack.length - 1] !== "(") return false;
        stack.pop();
        break;
      case "}":
        if (stack[stack.length - 1] !== "{") return false;
        stack.pop();
        break;
      case "]":
        if (stack[stack.length - 1] !== "[") return false;
        stack.pop();
        break;
    }
  }
  return stack.length === 0;
}
```
