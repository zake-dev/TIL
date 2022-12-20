# [LeetCode] 415. Add Strings

## Problem

> Given two non-negative integers, `num1` and `num2` represented as string, return _the sum of `num1` and `num2` as a string_.
> You must solve the problem without using any built-in library for handling large integers (such as `BigInteger`). You must also not convert the inputs to integers directly.
> [[LeetCode] 415. Add Strings](https://leetcode.com/problems/add-strings/?envType=study-plan&id=data-structure-ii)

## Solution

- Ensure the length of `num1` is greater or equal to `num2`.
- Convert two number strings to reversed array.
- Calculate `carry` and `sum` digit by digit.
- Append remaining `carry` and `digits` in `num1`.
- Return reversed, joined `digits` derived from above.
- Runtime Complexity: **O(n)**

```typescript
function addStrings(num1: string, num2: string): string {
  if (num1.length < num2.length) return addStrings(num2, num1);
  const digits1 = num1.split("").reverse();
  const digits2 = num2.split("").reverse();

  let carry = 0;
  for (let i = 0; i < digits2.length; i++) {
    const [digit1, digit2] = [digits1[i], digits2[i]].map((s) => +s);
    const sum = digit1 + digit2 + carry;
    carry = sum >= 10 ? 1 : 0;
    digits1[i] = (sum % 10).toString();
  }

  for (let i = digits2.length; carry || i < digits1.length; i++) {
    const sum = +(digits1[i] ?? 0) + carry;
    carry = sum >= 10 ? 1 : 0;
    digits1[i] = (sum % 10).toString();
  }

  return digits1.reverse().join("");
}
```

## Other's Solution

- Similar logic but it accesses each `digit` directly from `num1` and `num2`.
- Combine result string directly as well.
- Small trick to improve floor calculation with `~~` bit operator rather than using `Math.floor`.
- Runtime Complexity: **O(n)**

```typescript
function addStrings(num1: string, num2: string): string {
  let i = num1.length - 1;
  let j = num2.length - 2;
  let sum = "";
  let carry = 0;
  while (i >= 0 || j >= 0 || carry > 0) {
    const digit1 = i < 0 ? 0 : +num1[i];
    const digit2 = j < 0 ? 0 : +num2[j];
    const digitSum = digit1 + digit2 + carry;
    sum = `${digitSum % 10}${sum}`;
    carry = ~~(digitSum / 10);
    i--;
    j--;
  }
  return sum;
}
```
