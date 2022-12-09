# [LeetCode] 653. Two Sum IV - Input is a BST

## Problem

> [[LeetCode] Two Sum IV - Input is a BST](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/description/?envType=study-plan&id=data-structure-i)

## Solution

- Use hash set to record a pair while traversing the tree.
- Traverse through the tree, if there is a pair recorded in the hash set, return `true`.
- Otherwise, return `false`.
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

function findTarget(root: TreeNode | null, k: number): boolean {
  function find(
    node: TreeNode | null,
    k: number,
    hashSet: Set<number>
  ): boolean {
    if (!node) return false;
    if (hashSet.has(node.val)) return true;
    hashSet.add(k - node.val);
    return find(node.left, k, hashSet) || find(node.right, k, hashSet);
  }

  return find(root, k, new Set());
}
```

## Other's Solution

- No other impressive solutions found.
