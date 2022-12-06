# [LeetCode] 94. Binary Tree Inorder Traversal

## Problem

> Given the `root` of a binary tree, return the _inorder traversal of its nodes' values_.
> [[LeetCode] 94. Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/?envType=study-plan&id=data-structure-i)

## Solution

- Inorder traversal searches `left-most leaf node - root - right leaf node` in order.
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

function inorderTraversal(root: TreeNode | null): number[] {
  function inorder(node: TreeNode | null, result: number[]): number[] {
    if (!node) return [];
    inorder(node.left, result);
    result.push(node.val);
    inorder(node.right, result);
    return result;
  }

  return inorder(root, []);
}
```

## Other's Solution

- Iterative version of inorder traversal.
- This version is more readable and understandable how inorder traversal works through.
- Runtime Complexity: **O(n)**

```typescript
function inorderTraversal(root: TreeNode | null): number[] {
  if (!root) return [];

  const stack: TreeNode[] = [];
  const result: number[] = [];

  pushAllLeft(root, stack);
  while (stack.length) {
    const node = stack.pop();
    result.push(node!.val);
    pushAllLeft(node!.right, stack);
  }

  return result;
}

function pushAllLeft(node: TreeNode | null, stack: TreeNode[]) {
  while (node) {
    stack.push(node);
    node = node.left;
  }
}
```
