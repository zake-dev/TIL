# [[LeetCode] 102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal)

# Solution - TypeScript

```typescript
function levelOrder(root: TreeNode | null): number[][] {
  const levels: number[][] = [];

  function bfs(node: TreeNode | null, level: number = 0) {
    if (node === null) return;
    if (levels.length === level) levels.push([]);
    levels[level].push(node.val);
    if (node.left !== null) bfs(node.left, level + 1);
    if (node.right !== null) bfs(node.right, level + 1);
  }
  bfs(root);

  return levels;
}
```
