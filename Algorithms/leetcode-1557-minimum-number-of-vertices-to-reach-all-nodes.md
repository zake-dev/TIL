# [LeetCode] 1557. Minimum Number of Vertices to Reach All Nodes

## Problem

> Given a **directed acyclic graph**, with `n` vertices numbered from `0` to `n-1`, and an array `edges` where `edges[i] = [fromi, toi]` represents a directed edge from node `fromi` to node `toi`.
> Find _the smallest set of vertices from which all nodes in the graph are reachable. It's guaranteed that a unique solution exists_.
> Notice that you can return the vertices in any order.
> [[LeetCode] 1557. Minimum Number of Vertices to Reach All Nodes](https://leetcode.com/problems/minimum-number-of-vertices-to-reach-all-nodes/description/)

## Solution

- As the given graph is a directed acyclic graph, a set of vertices that does not have any other directed edges from others will be able to reach all nodes.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function findSmallestSetOfVertices(n: number, edges: number[][]): number[] {
  const verticesHavingIncomingEdge = toSet(edges);
  return Array.from({ length: n }, (_, i) => i).filter(
    (i) => !verticesHavingIncomingEdge.has(i)
  );
}

function toSet(edges: number[][]): Set<number> {
  const set = new Set<number>();
  for (const [_, to] of edges) set.add(to);
  return set;
}
```

## Other's Solution

- All uses same approaches.
