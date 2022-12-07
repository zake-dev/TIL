# [LeetCode] 112. Path Sum

## Problem

> Given the `root` of a binary tree and an integer `targetSum`, return`true` if the tree has a **root-to-leaf** path such that adding up all the values along the path equals `targetSum`.
> A **leaf** is a node with no children.
> [[LeetCode] 112. Path Sum](https://leetcode.com/problems/path-sum/?envType=study-plan&id=data-structure-i)

## Solution

- Calculate `path sum` by using `DFS Algorithm`.
- Only check _the `path` sum is equal to `targetSum`_ when the `node` is a **leaf node**.
- Handle edge case: _if `root === null`, return `false`_.
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

function hasPathSum(root: TreeNode | null, targetSum: number): boolean {
  function traverse(node: TreeNode | null, sum: number): boolean {
    if (!node) return false;
    if (!node.left && !node.right) return sum + node.val === targetSum;
    return (
      traverse(node.left, sum + node.val) ||
      traverse(node.right, sum + node.val)
    );
  }

  if (!root) return false;
  return traverse(root, 0);
}
```

## Other's Solution

- Shorter version without inner function.
- It uses `targetSum` itself to compare with `TreeNode.val`.
- Instead of adding up the `val`, subtract the `val` from the `targetSum`.
- Runtime Complexity: **O(n)**

```typescript
function hasPathSum(root: TreeNode | null, targetSum: number): boolean {
  if (!root) return false;
  if (!root.left && !root.right) return targetSum === root.val;
  return (
    hasPathSum(root.left, targetSum - root.val) ||
    hasPathSum(root.right, targetSum - root.val)
  );
}
```
