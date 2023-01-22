# [LeetCode] 1281. Subtract the Product and Sum of Digits of an Integer

## Problem

> Given an integer number `n`, return the difference between the product of its digits and the sum of its digits.
> [[LeetCode] 1281. Subtract the Product and Sum of Digits of an Integer](https://leetcode.com/problems/subtract-the-product-and-sum-of-digits-of-an-integer/description/?envType=study-plan&id=programming-skills-i)

## Solution

- Convert the given `n` to array of digits.
- Find `sum` and `product` of `digits`.
- Return subtraction of `product` by `sum`.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function subtractProductAndSum(n: number): number {
  const digits = n
    .toString()
    .split("")
    .map((n) => +n);
  const sum = digits.reduce((a, b) => a + b);
  const product = digits.reduce((a, b) => a * b);
  return product - sum;
}
```

## Other's Solution

- This is a simple implementation problem.
