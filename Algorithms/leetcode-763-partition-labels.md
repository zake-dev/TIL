# [LeetCode] 763. Partition Labels

## Problem

> You are given a string `s`. We want to partition the string into as many parts as possible so that each letter appears in at most one part.
> Note that the partition is done so that after concatenating all the parts in order, the resultant string should be `s`.
> Return _a list of integers representing the size of these parts_.
> [[LeetCode] 763. Partition Labels](https://leetcode.com/problems/partition-labels/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Failed to solve my own. This is my version of referred solution.
- Firstly, create a dictionary, `Map` in TypeScript, find _the last index_ of each character appears in the given `s`.
- Use two pointers to calculate partition size. `start` and `end` is set to initial partition size. Iterate over `start` to `end`, if the last index of `s[i]` is bigger than `end`, extend `end`.
- Push computed partition size and calculate next until the end of `s`.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function partitionLabels(s: string): number[] {
  const sizes: number[] = [];
  const lastIndices = getLastIndices(s);

  let start = 0;
  while (start < s.length) {
    let end = lastIndices.get(s[start]);
    for (let i = start + 1; i < end; i++)
      if (lastIndices.get(s[i]) > end) end = lastIndices.get(s[i]);
    sizes.push(end - start + 1);
    start = end + 1;
  }

  return sizes;
}

function getLastIndices(s: string): Map<string, number> {
  const lastIndices = new Map<string, number>();
  for (let i = 0; i < s.length; i++) lastIndices.set(s[i], i);
  return lastIndices;
}
```

## Other's Solution

- There are some optimized solutions than this, but I think readability is more important than make solution faster if the solution passes the constraints.
