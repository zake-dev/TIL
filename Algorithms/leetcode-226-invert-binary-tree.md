# [LeetCode] 226. Invert Binary Tree

## Problem

> Given the `root` of a binary tree, invert the tree, and return _its root_.
> [[LeetCode] 226. Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/?envType=study-plan&id=data-structure-i)

## Solution

- Swap `left` and `right` of the given `node`.
- Operate recursively through the tree.
- Runtime Complexity: **O(n)**

```typescript
/**
 * Definition for a binary tree node.
 * class TreeNode {
 *     val: number
 *     left: TreeNode | null
 *     right: TreeNode | null
 *     constructor(val?: number, left?: TreeNode | null, right?: TreeNode | null) {
 *         this.val = (val===undefined ? 0 : val)
 *         this.left = (left===undefined ? null : left)
 *         this.right = (right===undefined ? null : right)
 *     }
 * }
 */

function invertTree(node: TreeNode | null): TreeNode | null {
  if (!node) return node;

  const temp = node.left;
  node.left = node.right;
  node.right = temp;
  invertTree(node.left);
  invertTree(node.right);

  return node;
}
```

## Other's Solution

- Same logic but simple version.
- `Destructuring Syntax` and `Divide and Conquer Algorithm` made a magic.
- Runtime Complexity: **O(n)**

```typescript
function invertTree(node: TreeNode | null): TreeNode | null {
  if (node)
    [node.left, node.right] = [invertTree(node.right), invertTree(node.left)];
  return node;
}
```
