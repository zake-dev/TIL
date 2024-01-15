# [[LeetCode] 122. Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description)

# Solution - TypeScript

```typescript
function maxProfit(prices: number[]): number {
  let max = 0;
  for (let i = 1; i < prices.length; i++) {
    const profit = prices[i] - prices[i - 1];
    max += profit > 0 ? profit : 0;
  }
  return max;
}
```
