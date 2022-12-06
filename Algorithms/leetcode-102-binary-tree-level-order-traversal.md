# [LeetCode] 102. Binary Tree Level Order Traversal

## Problem

> Given the `root` of a binary tree, return _the level order traversal of its nodes' values_. (i.e., from left to right, level by level).
> [[LeetCode] 102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/?envType=study-plan&id=data-structure-i)

## Solution

- Traverse the tree in preorder.
- Collect `level` of current node together.
- Use `Map` object to collect _nodes by level_.
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

function levelOrder(root: TreeNode | null): number[][] {
  function traverse(
    node: TreeNode | null,
    level: number,
    nodesByLevel: Map<number, number[]>
  ): Map<number, number[]> {
    if (!node) return nodesByLevel;
    if (!nodesByLevel.has(level + 1)) nodesByLevel.set(level + 1, []);

    const nodesInSameLevel = nodesByLevel.get(level + 1);
    nodesInSameLevel?.push(node.val);
    traverse(node.left, level + 1, nodesByLevel);
    traverse(node.right, level + 1, nodesByLevel);

    return nodesByLevel;
  }

  return [...traverse(root, 0, new Map()).values()];
}
```

## Other's Solution

- As the `level(height)` of the tree is as same as `index` of result array, `Map` object can be replaced with `number[][]`.
- Runtime Complexity: **O(n)**

```typescript
function levelOrder(root: TreeNode | null): number[][] {
  function traverse(
    node: TreeNode | null,
    level: number,
    result: number[][]
  ): number[][] {
    if (!node) return result;
    if (level >= result.length) result.push([]);

    result[level].push(node.val);
    traverse(node.left, level + 1, result);
    traverse(node.right, level + 1, result);

    return result;
  }

  return traverse(root, 0, []);
}
```
