# [[LeetCode] 150. Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/description)

# Solution - TypeScript

```typescript
function evalRPN(tokens: string[]): number {
  const stack: number[] = [];
  for (const token of tokens) {
    if (!isOperator(token)) {
      stack.push(+token);
      continue;
    }

    const [second, first] = [stack.pop(), stack.pop()];
    switch (token) {
      case "+":
        stack.push(first + second);
        break;
      case "-":
        stack.push(first - second);
        break;
      case "*":
        stack.push(first * second);
        break;
      case "/":
        const result = first / second;
        stack.push(result >= 0 ? Math.floor(result) : Math.ceil(result));
        break;
    }
  }
  return stack[0];
}

function isOperator(token: string): boolean {
  return ["+", "-", "*", "/"].includes(token);
}
```
