# [LeetCode] 997. Find a Town Judge

## Problem

> In a town, there are `n` people labeled from `1` to `n`. There is a rumor that one of these people is secretly the town judge.
> If the town judge exists, then:
> The town judge trusts nobody.
> Everybody (except for the town judge) trusts the town judge.
> There is exactly one person that satisfies properties 1 and 2.
> You are given an array `trust` where `trust[i] = [ai, bi]` representing that the person labeled `ai` trusts the person labeled bi.
> Return _the label of the town judge if the town judge exists and can be identified, or return `-1` otherwise_.
> [[LeetCode] 997. Find a Town Judge](https://leetcode.com/problems/find-the-town-judge/description/)

## Solution

- Find a town judge step by step.
- Count how many times each person get trusted.
- Find who is trusted by all people, if not return `-1`.
- Double check the person trusted by all does not trust any other people in a town.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function findJudge(n: number, trust: number[][]): number {
  if (n === 1 && !trust.length) return 1;

  const personTrustedByAll = [...countTrust(trust).entries()].find(
    ([_, count]) => count === n - 1
  );
  if (!personTrustedByAll) return -1;
  return validateTownJudge(personTrustedByAll[0], trust);
}

function countTrust(trust: number[][]): Map<number, number> {
  const counter = new Map<number, number>();
  for (const [_, b] of trust) {
    const count = (counter.get(b) ?? 0) + 1;
    counter.set(b, count);
  }
  return counter;
}

function validateTownJudge(id: number, trust: number[][]): number {
  for (const [a, _] of trust) if (a === id) return -1;
  return id;
}
```

## Other's Solution

- Similar approaches.
