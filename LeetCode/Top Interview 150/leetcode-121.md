# [[LeetCode] 121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description)

# Solution - TypeScript

```typescript
function maxProfit(prices: number[]): number {
  let min = prices[0];
  let max = 0;
  for (const price of prices) {
    if (price < min) min = price;
    if (price - min > max) max = price - min;
  }
  return max;
}
```
