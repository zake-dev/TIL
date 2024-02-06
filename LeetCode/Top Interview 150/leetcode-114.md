# [[LeetCode] 114. Flatten Binary Tree to Linked List](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/description)

# Solution - TypeScript

```typescript
function flatten(root: TreeNode | null): void {
  function dfs(root: TreeNode | null): TreeNode | null {
    if (root === null) return null;

    const leftTail = dfs(root.left);
    const rightTail = dfs(root.right);

    if (root.left) {
      leftTail.right = root.right;
      root.right = root.left;
      root.left = null;
    }

    return rightTail ?? leftTail ?? root;
  }

  dfs(root);
}
```
