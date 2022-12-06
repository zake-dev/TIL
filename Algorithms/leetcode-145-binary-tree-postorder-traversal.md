# [LeetCode] 145. Binary Tree Postorder Traversal

## Problem

> Given the `root` of a binary tree, return _the postorder traversal of its nodes' values_.
> [[LeetCode] 145. Binary Tree Postorder Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal/?envType=study-plan&id=data-structure-i)

## Solution

- Postorder traversal visits node in order of `left - right - root`.
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

function postorderTraversal(root: TreeNode | null): number[] {
  function postorder(node: TreeNode | null, result: number[]) {
    if (!node) return [];

    postorder(node.left, result);
    postorder(node.right, result);
    result.push(node.val);

    return result;
  }

  return postorder(root, []);
}
```

## Other's Solution

- Iterative version of postorder traversal is quite verbose. It's not recommended to implement without recursion if there is no reason.
