# [[LeetCode] 399. Evaluate Division](https://leetcode.com/problems/evaluate-division/description)

# Solution - TypeScript

```typescript
function calcEquation(
  equations: string[][],
  values: number[],
  queries: string[][]
): number[] {
  function buildGraph(): Map<string, Map<string, number>> {
    const graph = new Map<string, Map<string, number>>();
    for (let i = 0; i < equations.length; i++) {
      const [from, to] = equations[i];
      if (!graph.has(from)) graph.set(from, new Map());
      if (!graph.has(to)) graph.set(to, new Map());
      graph.get(from).set(to, values[i]);
      graph.get(to).set(from, 1 / values[i]);
    }
    return graph;
  }

  const graph = buildGraph();
  function calculateDivision(
    from: string,
    to: string,
    visited: Set<string>
  ): number {
    if (!graph.has(from) || !graph.has(to)) return -1;
    if (from === to) return 1;
    for (const [neighbor, weight] of graph.get(from).entries()) {
      if (visited.has(neighbor)) continue;
      visited.add(neighbor);
      const division = calculateDivision(neighbor, to, visited) * weight;
      if (division > 0) return division;
    }
    return -1;
  }

  return queries.map(([from, to]) => calculateDivision(from, to, new Set()));
}
```
