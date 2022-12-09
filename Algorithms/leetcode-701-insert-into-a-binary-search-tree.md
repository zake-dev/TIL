# [LeetCode] 701. Insert into a Binary Search Tree

## Problem

> You are given the `root` node of a binary search tree (BST) and a `value` to insert into the tree. Return _the root node of the BST after the insertion_. It is **guaranteed** that the new value does not exist in the original BST.
> **Notice** that there may exist multiple valid ways for the insertion, as long as the tree remains a BST after insertion. You can return **any of them**.
> [[LeetCode] 701. Insert into a Binary Search Tree](https://leetcode.com/problems/insert-into-a-binary-search-tree/description/?envType=study-plan&id=data-structure-i)

## Solution

- Find the leaf node, put a new `TreeNode(val)` left if the given `val` is smaller than the value of the leaf node. Else, put a new `TreeNode(val)` right.
- Runtime Complexity: **O(logn)**

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

function insertIntoBST(root: TreeNode | null, val: number): TreeNode | null {
  if (!root) return new TreeNode(val);
  if (!root.left && val < root.val) root.left = new TreeNode(val);
  if (!root.right && val > root.val) root.right = new TreeNode(val);
  if (val < root.val) insertIntoBST(root.left, val);
  if (val > root.val) insertIntoBST(root.right, val);
  return root;
}
```

## Other's Solution

- Shorter version. I am always surprised that there is a shorter version of recursive version of mine! :O
- Runtime Complexity: **O(logn)**

```typescript
function insertIntoBST(root: TreeNode | null, val: number): TreeNode | null {
  if (!root) return new TreeNode(val);
  if (val < root.val) root.left = insertIntoBST(root.left, val);
  else root.right = insertIntoBST(root.right, val);
  return root;
}
```
