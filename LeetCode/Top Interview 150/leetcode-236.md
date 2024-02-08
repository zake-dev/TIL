# [[LeetCode] 236. Lowest Common ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description)

# Solution - TypeScript

```typescript
function lowestCommonAncestor(
  root: TreeNode | null,
  p: TreeNode | null,
  q: TreeNode | null
): TreeNode | null {
  if (root === null || root === p || root === q) return root;

  const left = lowestCommonAncestor(root.left, p, q);
  const right = lowestCommonAncestor(root.right, p, q);

  const isLowestCommonAncestor =
    (left === p && right === q) || (left === q && right === p);
  return isLowestCommonAncestor ? root : left ?? right;
}
```
