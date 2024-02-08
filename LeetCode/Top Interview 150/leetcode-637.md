# [[LeetCode] 637. Average of Levels in Binary Tree](https://leetcode.com/problems/average-of-levels-in-binary-tree/description)

# Solution - TypeScript

```typescript
function averageOfLevels(root: TreeNode | null): number[] {
  const averages: number[][] = [];

  function bfs(node: TreeNode | null, level: number = 0) {
    if (node === null) return;
    if (averages.length === level) averages.push([]);
    averages[level].push(node.val);
    bfs(node.left, level + 1);
    bfs(node.right, level + 1);
  }
  bfs(root);

  return averages.map(
    (values) => values.reduce((a, b) => a + b) / values.length
  );
}
```
