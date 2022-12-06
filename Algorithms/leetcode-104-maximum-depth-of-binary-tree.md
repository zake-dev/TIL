# [LeetCode] 104. Maximum Depth of Binary Tree

## Problem

> Given the `root` of a binary tree, return _its maximum depth_.
> A binary tree's **maximum depth** is the number of nodes along the longest path from the root node down to the farthest leaf node.
> [[LeetCode] 104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/?envType=study-plan&id=data-structure-i)

## Solution

- Traverse the tree by recursion, find the `max depth`.
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

function maxDepth(root: TreeNode | null): number {
  function traverse(
    node: TreeNode | null,
    depth: number,
    maxDepth: number
  ): number {
    if (!node) return maxDepth;

    maxDepth = Math.max(maxDepth, depth);
    return Math.max(
      traverse(node.left, depth + 1, maxDepth),
      traverse(node.right, depth + 1, maxDepth)
    );
  }

  return traverse(root, 1, 0);
}
```

## Other's Solution

- Brilliant solution! This combines `max depth` logic and `depth` at once.
- Keep counting through the tree, if `node == null` return `0`.
- Adding those `depth` and return _maximum value_.
- Runtime Complexity: **O(n)**

```typescript
function maxDepth(node: TreeNode | null): number {
  if (!node) return 0;
  const leftMax = maxDepth(node.left);
  const rightMax = maxDepth(node.right);
  return Math.max(leftMax, rightMax) + 1;
}
```
