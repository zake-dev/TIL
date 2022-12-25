# [LeetCode] 43. Multiply Strings

## Problem

> Given two non-negative integers `num1` and `num2` represented as strings, return the product of `num1` and `num2`, also represented as a string.
> Note: You must not use any built-in BigInteger library or convert the inputs to integer directly.
> [[LeetCode] 43. Multiply Strings](https://leetcode.com/problems/multiply-strings/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Mimic the way we calculate product of two positive numbers in the real world.
  - Put bigger number above, smaller number below.
  - Calculate product of `num1` and 1-digit of `num2`. Add trailing zeros by its position of digit.
  - Add all products of digits.
- Implemented 3 functions following above logic.
- Time complexity: **O(n^2)** Space Complexity: **O(n)**

```typescript
function multiply(num1: string, num2: string): string {
  if (num1.length < num2.length) return multiply(num2, num1);

  let result = "0";
  for (let i = 0; i < num2.length; i++) {
    const trailingZero = new Array(num2.length - i - 1).fill("0").join("");
    const digitMultiplied = `${multiplyDigit(num1, num2[i])}${trailingZero}`;
    result = add(result, digitMultiplied);
  }

  return result;
}

function multiplyDigit(num: string, digit: string): string {
  if (digit === "0") return "0";

  let result = "";
  let carry = 0;
  let i = num.length - 1;
  while (i >= 0 || carry > 0) {
    const multiplied = +(num[i] ?? 0) * +digit + carry;
    carry = ~~(multiplied / 10);
    result = `${multiplied % 10}${result}`;
    i--;
  }
  return result;
}

function add(num1: string, num2: string): string {
  let result = "";
  let carry = 0;
  let i = num1.length - 1;
  let j = num2.length - 1;
  while (i >= 0 || j >= 0 || carry > 0) {
    const digit1 = i < 0 ? 0 : +num1[i];
    const digit2 = j < 0 ? 0 : +num2[j];
    const sum = digit1 + digit2 + carry;
    carry = ~~(sum / 10);
    result = `${sum % 10}${result}`;
    i--;
    j--;
  }
  return result;
}
```

## Other's Solution

- More organized, concise, intuitive solution.
- It uses similar approach, but break logic down smaller.
- The logic assumes that:
  - Product of two 1-digit numbers are always less than `100`.
  - The result of production of `num1[i]` and `num2[j]` will added in position `[i + j, i + j + 1]` which is `digits[i + j] = product / 10` and `digits[i + j + 1] = product % 10`.
- After pushing all digit productions into `digits`, remove leading zeros.
- Time Complexity: **O(n^2)**, Space Complexity: **O(m + n) = O(n)**

```typescript
function multiply(num2: string, num2: string): string {
  const [m, n] = [num1.length, num2.length];
  const digits = new Array(m + n).fill(0);

  for (let i = m - 1; i >= 0; i--) {
    for (let j = n - 1; j >= 0; j--) {
      const product = +num1[i] * +num2[j];
      const [p1, p2] = [i + j, i + j + 1];
      const sum = product + digits[p2];

      digits[p1] += ~~(sum / 10);
      digits[p2] = sum % 10;
    }
  }

  const sliceIndex = digits.findIndex((n) => !!n);
  return sliceIndex > -1 ? digits.slice(sliceIndex).join("") : "0";
}
```
