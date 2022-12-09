# [LeetCode] 98. Validate Binary Search Tree

## Problem

> Given the `root` of a binary tree, _determine if it is a valid binary search tree (BST)_.
> A **valid BST** is defined as follows:
>
> - The left subtree of a node contains only nodes with keys **less than** the node's key.
> - The right subtree of a node contains only nodes with keys **greater than** the node's key.
> - Both the left and right subtrees must also be binary search trees.

> [[LeetCode] 98. Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/?envType=study-plan&id=data-structure-i)

## Solution

- Traverse through the tree, pass the `validators` that the `node` should pass.
- Each `validator` represents who are the ancestor nodes from itself. The length of `validators` will be `logn` at maximum.
- `isLeftOf` checks the `node` has smaller value than its ancestor.
- `isRightOf` checks the `node` has bigger value than its ancestor.
- Runtime Complexity: **O(n\*logn)**

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

type validator = (node: TreeNode) => boolean;

function isValidBST(root: TreeNode | null): boolean {
  function allValid(node: TreeNode | null, validators: validator[]): boolean {
    if (!node) return true;
    if (!validators.every((validator) => validator(node))) return false;
    if (node.left && node.left.val >= node.val) return false;
    if (node.right && node.right.val <= node.val) return false;
    return (
      allValid(node.left, [...validators, isLeftOf(node.val)]) &&
      allValid(node.right, [...validators, isRightOf(node.val)])
    );
  }

  return allValid(root, []);
}

function isLeftOf(n: number): validator {
  return (node: TreeNode) => node.val < n;
}

function isRightOf(n: number) {
  return (node: TreeNode) => node.val > n;
}
```

## Other's Solution

- Another recursive version but faster and less using memory.
- It passes `left` and `right` values as range limit of each node. Every `node` should satisfy that the value of the `node` is between `left` and `right`.
- Runtime Complexity: **O(n)**

```typescript
function isValidBST(root: TreeNode | null): boolean {
  function validate(
    node: TreeNode | null,
    left: number,
    right: number
  ): boolean {
    if (!node) return true;
    if (left >= node.val || right <= node.val) return false;
    return (
      validate(node.left, left, node.val) &&
      validate(node.right, node.val, right)
    );
  }

  return validate(root, -Infinity, Infinity);
}
```
