# [[LeetCode] 199. Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/description)

# Solution - TypeScript

```typescript
function rightSideView(root: TreeNode | null): number[] {
  const view: number[] = [];

  function bfs(node: TreeNode | null, level: number = 0) {
    if (node === null) return;
    if (view.length === level) view.push(node.val);
    bfs(node.right, level + 1);
    bfs(node.left, level + 1);
  }
  bfs(root);

  return view;
}
```
