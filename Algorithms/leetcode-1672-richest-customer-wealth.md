# [LeetCode] 1672. Richest Customer Wealth

## Problem

> You are given an `m x n` integer grid `accounts` where `accounts[i][j]` is the amount of money the `i​​​​​​​​​​​th`​​​​ customer has in the `j​​​​​​​​​​​th​​​​` bank. Return _the **wealth** that the richest customer has_.
> A customer's **wealth** is the amount of money they have in all their bank accounts. The richest customer is the customer that has the maximum **wealth**.
> [[LeetCode] 1672. Richest Customer Wealth](https://leetcode.com/problems/richest-customer-wealth/description/?envType=study-plan&id=programming-skills-i)

## Solution

- Brute-Force algorithm applied.
- Convert all account into its sum, then find max wealth from it.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function maximumWealth(accounts: number[][]): number {
  return Math.max(...accounts.map(arraySum));
}

function arraySum(array: number[]): number {
  return array.reduce((a, b) => a + b);
}
```

## Other's Solution

- All uses same approaches.
