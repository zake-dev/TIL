# [[LeetCode] 133. Clone Graph](https://leetcode.com/problems/clone-graph)

# Solution - TypeScript

```typescript
function cloneGraph(node: Node | null): Node | null {
  if (node === null) return null;

  const cloneMap = new Map<Node, Node>();
  const visited = new Set<Node>();

  function createClones(node: Node | null): void {
    if (visited.has(node)) return;
    visited.add(node);
    cloneMap.set(node, new Node(node.val));
    node.neighbors.forEach((neighbor) => createClones(neighbor));
  }
  createClones(node);

  visited.clear();
  function setNeighbors(node: Node | null): void {
    if (visited.has(node)) return;
    visited.add(node);
    const clone = cloneMap.get(node);
    node.neighbors.forEach((neighbor) => {
      clone.neighbors.push(cloneMap.get(neighbor));
      setNeighbors(neighbor);
    });
  }
  setNeighbors(node);

  return cloneMap.get(node);
}
```
