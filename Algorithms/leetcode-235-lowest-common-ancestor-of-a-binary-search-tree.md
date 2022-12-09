# [LeetCode] 235. Lowest Common Ancestor of a Binary Search Tree

## Problem

> Given a binary search tree (BST), find the lowest common ancestor (LCA) node of two given nodes in the BST.
> According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes `p` and `q` as the lowest node in `T` that has both `p` and `q` as descendants (where we allow **a node to be a descendant of itself**).”
> [[LeetCode] 235. Lowest Common Ancestor of a Binary Search Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/?envType=study-plan&id=data-structure-i)

## Solution

- Ensure `p.val < q.val`.
- If the `node(root)` is greater than `p` and smaller than `q`, `node(root)` is _the lowest common ancestor_.
- For this problem, you should handle _if the `node(root)` is equal to `p` or `q`_ as well.
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

function lowestCommonAncestor(
  root: TreeNode | null,
  p: TreeNode | null,
  q: TreeNode | null
): TreeNode | null {
  if (p.val > q.val) return lowestCommonAncestor(root, q, p);
  if (root === p || root === q) return root;
  if (p.val < root.val && root.val < q.val) return root;
  if (q.val < root.val) return lowestCommonAncestor(root.left, p, q);
  else return lowestCommonAncestor(root.right, p, q);
}
```

## Other's Solution

- Easier filtering by organizing `if statement` efficiently.
- Runtime Complexity: **O(logn)**

```typescript
function lowestCommonAncestor(
  root: TreeNode | null,
  p: TreeNode | null,
  q: TreeNode | null
): TreeNode | null {
  if (p.val < root.val && q.val < root.val) {
    return lowestCommonAncestor(root.left, p, q);
  }
  if (p.val > root.val && q.val > root.val) {
    return lowestCommonAncestor(root.right, p, q);
  }
  return root;
}
```
