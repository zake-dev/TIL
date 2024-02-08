# [[LeetCode] 103. Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/description)

# Solution - TypeScript

```typescript
function zigzagLevelOrder(root: TreeNode | null): number[][] {
  const levels: number[][] = [];

  function bfs(node: TreeNode | null, level: number = 0) {
    if (node === null) return;
    if (levels.length === level) levels.push([]);

    if (level % 2 === 0) levels[level].push(node.val);
    else levels[level].unshift(node.val);

    if (node.left !== null) bfs(node.left, level + 1);
    if (node.right !== null) bfs(node.right, level + 1);
  }
  bfs(root);

  return levels;
}
```
