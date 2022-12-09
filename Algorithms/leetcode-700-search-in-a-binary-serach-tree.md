# [LeetCode] 700. Search in a Binary Search Tree

## Problem

> You are given the `root` of a binary search tree (BST) and an integer `val`.
> Find the node in the BST that the node's value equals `val` and return the subtree rooted with that node. If such a node does not exist, return `null`.
> [[LeetCode] 700. Search in a Binary Search Tree](https://leetcode.com/problems/search-in-a-binary-search-tree/description/?envType=study-plan&id=data-structure-i)

## Solution

- Binary Search Tree(BST) is an ordered tree. Each node can only have maximum 2 nodes, and always the value of the left node is smaller than its parent, the value of the right node is bigger than its parent.
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

function searchBST(root: TreeNode | null, val: number): TreeNode | null {
  if (!root) return null;
  if (root.val === val) return root;
  if (root.val < val) return searchBST(root.right, val);
  return searchBST(root.left, val);
}
```

## Other's Solution

- Iterative version.
- Runtime Complexity: **O(logn)**

```typescript
function searchBST(root: TreeNode | null, val: number): TreeNode | null {
  let current = root;
  while (current && current.val !== val) {
    if (current.val < val) current = current.right;
    else current = current.left;
  }
  return current;
}
```
