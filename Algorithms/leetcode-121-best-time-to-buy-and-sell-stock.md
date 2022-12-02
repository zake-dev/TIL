# [LeetCode] 121. Best Time to Buy and Sell Stock

## Problem

> You are given an array `prices` where `prices[i]` is the price of a given stock on the <code>i<sup>th</sup></code> day.
> You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.
> Return the _maximum profit you can achieve from this transaction_. If you cannot achieve any profit, return `0`.
> [[LeetCode] 121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

## Solution

- Iterate over prices, keep tracking the lowest price.
- `profit` is `current price - lowest`.
- Update `maximum profit` with `profit`.
- Runtime Complexity: **O(n)**

```typescript
function maxProfit(prices: number[]): number {
  let lowest = prices[0];
  let maxProfit = 0;
  for (const price of prices) {
    lowest = Math.min(lowest, price);
    maxProfit = Math.max(maxProfit, price - lowest);
  }
  return maxProfit;
}
```

## Other's Solution

- Most solutions are similar to mine.
