# [[LeetCode] 230. Kth Smallest Element in BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/description)

# Solution - TypeScript

```typescript
function kthSmallest(root: TreeNode | null, k: number): number {
  const values: number[] = [];

  function inorder(node: TreeNode | null): void {
    if (node === null) return;

    inorder(node.left);
    values.push(node.val);
    inorder(node.right);
  }
  inorder(root);

  return values[k - 1];
}
```
