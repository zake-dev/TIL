# [[LeetCode] 134. Gas Station](https://leetcode.com/problems/gas-station/description)

# Solution - TypeScript

```typescript
function canCompleteCircuit(gas: number[], cost: number[]): number {
  let totalGas = 0;
  let totalCost = 0;
  let currentGas = 0;
  let startingIndex = 0;
  for (let i = 0; i < gas.length; i++) {
    totalGas += gas[i];
    totalCost += cost[i];

    currentGas += gas[i] - cost[i];
    if (currentGas < 0) {
      startingIndex = i + 1;
      currentGas = 0;
    }
  }
  return totalGas < totalCost ? -1 : startingIndex;
}
```
