# [LeetCode] 236. Lowest Common Ancestor of a Binary Tree

## Problem

> Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.
> According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes `p` and `q` as the lowest node in `T` that has both `p` and `q` as descendants (where we allow **a node to be a descendant of itself**).”
> [[LeetCode] 236. Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Using DFS algorithm. Find `p` and `q`.
- Function call stack of the lowest common ancestor node will have two cases.
  1. `p` or `q` is a descendant node of other.
  2. `p` and `q` is a descendant node of `r`.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function lowestCommonAncestor(
  root: TreeNode | null,
  p: TreeNode | null,
  q: TreeNode | null
): TreeNode | null {
  if (!root) return null;
  if (root === p || root === q) return root;
  const left = lowestCommonAncestor(root.left, p, q);
  const right = lowestCommonAncestor(root.right, p, q);

  if (left && right) return root;
  return left ?? right;
}
```

## Other's Solution

- Above solution is the most concise one.
