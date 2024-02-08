# [[LeetCode] 98. Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/description)

# Solution - TypeScript

```typescript
function isValidBST(root: TreeNode | null): boolean {
  if (root === null) return true;

  function dfs(
    node: TreeNode | null,
    min: number = -Infinity,
    max: number = Infinity
  ): boolean {
    if (node === null) return true;
    if (node.val <= min || node.val >= max) return false;
    return dfs(node.left, min, node.val) && dfs(node.right, node.val, max);
  }

  return dfs(root);
}
```
