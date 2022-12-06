# [LeetCode] 144. Binary Tree Preorder Traversal

## Problem

> Given the `root` of a binary tree, return the preorder traversal of its nodes' values.
> [[LeetCode] 144. Binary Tree Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/description/?envType=study-plan&id=data-structure-i)

## Solution

- Preorder moves `root - left - left leaf - sibling right - right` order.
- For example, if the shape of the binary tree is `[1, null, 2, 3, 4 null, 5, 6]`, the correct preorder traversal is `[1, 2, 3, 5, 4, 6]`.
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

function preorderTraversal(root: TreeNode | null): number[] {
  function preorder(node: TreeNode | null, result: number[]): number[] {
    if (!node) return [];
    result.push(node.val);
    preorder(node.left, result);
    preorder(node.right, result);
    return result;
  }

  return preorder(root, []);
}
```

## Other's Solution

- Iterative version of preorder traversal.
- As `stack` is FILO data structure, push right node to the `stack` first, and then push the left one. It will handle right nodes after all left nodes are handled.
- Runtime Complexity: **O(n)**

```typescript
function preorderTraversal(root: TreeNode | null): number[] {
  if (!root) return [];

  const stack: TreeNode[] = [root];
  const result: number[] = [];

  while (stack.length) {
    const node = stack.pop();
    if (node?.right) stack.push(node.right);
    if (node?.left) stack.push(node.left);
    result.push(node!.val);
  }

  return result;
}
```
