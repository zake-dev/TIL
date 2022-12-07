# [LeetCode] 101. Symmetric Tree

## Problem

> Given the `root` of a binary tree, _check whether it is a mirror of itself_ (i.e., symmetric around its center).
> [[LeetCode] 101. Symmetric Tree](https://leetcode.com/problems/symmetric-tree/?envType=study-plan&id=data-structure-i)

## Solution

- Create a _level ordered tree values including `null`_.
- Check all levels are symmetric.
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

function isSymmetric(root: TreeNode | null): boolean {
  return levelOrderTraversal(root, 0, []).every(isSymmetricArray);
}

function levelOrderTraversal(
  node: TreeNode | null,
  level: number,
  result: (number | null)[][]
) {
  if (result.length <= level) result.push([]);

  result[level].push(node?.val ?? null);
  if (!node) return result;
  levelOrderTraversal(node.left, level + 1, result);
  levelOrderTraversal(node.right, level + 1, result);

  return result;
}

function isSymmetricArray(array: (number | null)[]): boolean {
  for (let i = 0; i < array.length; i++)
    if (array[i] !== array[array.length - 1 - i]) return false;
  return true;
}
```

## Other's Solution

- Way clear and direct solution using recursion.
- Search `TreeNode` through the tree, check _if mirror-positioned nodes are same_.
- Runtime Complexity: **O(n)**

```typescript
function isSymmetric(root: TreeNode | null): boolean {
  function isMirror(left: TreeNode | null, right: TreeNode | null) {
    if (!left && !right) return true;
    if (!left || !right) return false;
    if (left.val !== right.val) return false;
    return isMirror(left.left, right.right) && isMirror(left.right, right.left);
  }
  return isMirror(root, root);
}
```
