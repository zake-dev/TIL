# [LeetCode] 199. Binary Tree Right Side View

## Problem

> Given the `root` of a binary tree, imagine yourself standing on the **right side** of it, return _the values of the nodes you can see ordered from top to bottom_.
> [[LeetCode] 199. Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Traverse nodes with BFS, take right most value on the same level.
- Only store `node.val` there is no stored right side value in the `result`.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function rightSideView(root: TreeNode | null): number[] {
  function traverse(
    node: TreeNode | null,
    level: number,
    result: number[]
  ): number[] {
    if (!node) return result;
    if (result[level] === undefined) result[level] = node.val;
    traverse(node.right, level + 1, result);
    traverse(node.left, level + 1, result);
    return result;
  }

  return traverse(root, 0, []);
}
```

## Other's Solution

- No other brilliant solution found.
