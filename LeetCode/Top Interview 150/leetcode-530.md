# [[LeetCode] 530. Minimum Absolute Difference in BST](https://leetcode.com/problems/minimum-absolute-difference-in-bst/description)

# Solution - TypeScript

```typescript
function getMinimumDifference(root: TreeNode | null): number {
  const values: number[] = [];

  function inorder(node: TreeNode | null): void {
    if (node === null) return;

    inorder(node.left);
    values.push(node.val);
    inorder(node.right);
  }
  inorder(root);

  let min = Infinity;
  for (let i = 0; i < values.length - 1; i++)
    min = Math.min(min, values[i + 1] - values[i]);

  return min;
}
```
