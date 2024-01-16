# [[LeetCode] 135. Candy](https://leetcode.com/problems/candy/description)

# Solution - TypeScript

```typescript
function candy(ratings: number[]): number {
  let candies = Array(ratings.length).fill(1);
  for (let i = 1; i < ratings.length; i++)
    if (ratings[i] > ratings[i - 1]) candies[i] = candies[i - 1] + 1;
  for (let i = ratings.length - 1; i > 0; i--)
    if (ratings[i - 1] > ratings[i] && candies[i - 1] <= candies[i])
      candies[i - 1] = candies[i] + 1;
  return candies.reduce((a, b) => a + b);
}
```
