# [[LeetCode] 101. Symmetric Tree](https://leetcode.com/problems/symmetric-tree/description)

# Solution - TypeScript

```typescript
function isSymmetric(root: TreeNode | null): boolean {
  return isSameTree(root.left, invertBinaryTree(root.right));
}

function invertBinaryTree(root: TreeNode | null): TreeNode | null {
  if (root === null) return null;
  [root.left, root.right] = [root.right, root.left];
  invertBinaryTree(root.left);
  invertBinaryTree(root.right);
  return root;
}

function isSameTree(root1: TreeNode | null, root2: TreeNode | null): boolean {
  if (root1 === null && root2 === null) return true;
  if (root1?.val !== root2?.val) return false;
  return (
    isSameTree(root1?.left, root2?.left) &&
    isSameTree(root1?.right, root2?.right)
  );
}
```
