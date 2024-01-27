# [[LeetCode] 224. Basic Calculator](https://leetcode.com/problems/basic-calculator/description)

# Solution - TypeScript

```typescript
function calculate(s: string): number {
  const expression = s.replaceAll(" ", "");

  let result = 0;
  let sign = 1;
  let current = 0;
  const stack: number[] = [];

  for (const char of expression) {
    switch (char) {
      case "+":
      case "-":
        result += current * sign;
        current = 0;
        sign = char === "+" ? 1 : -1;
        continue;
      case "(":
        stack.push(result);
        stack.push(sign);
        result = 0;
        current = 0;
        sign = 1;
        continue;
      case ")":
        result += current * sign;
        const [prevSign, prevResult] = [stack.pop(), stack.pop()];
        result = prevResult + prevSign * result;
        sign = 1;
        current = 0;
        continue;
      default:
        current = current * 10 + +char;
        continue;
    }
  }

  return result + sign * current;
}
```
