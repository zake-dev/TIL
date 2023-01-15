# [LeetCode] 113. Path Sum II

## Problem

> Given the `root` of a binary tree and an integer `targetSum`, return _all **root-to-leaf** paths where the sum of the node values in the path equals `targetSum`. Each path should be returned as a list of the node **values**, not node references_.
> A **root-to-leaf** path is a path starting from the root and ending at any leaf node. A **leaf** is a node with no children.
> [[LeetCode] 113. Path Sum II](https://leetcode.com/problems/path-sum-ii/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Record path to leaf while traversing tree using DFS algorithm.
- If the `sum` of `path` is equal to `targetSum`, then add such `path` to `paths`.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function pathSum(root: TreeNode | null, targetSum: number): number[][] {
  const paths: number[][] = [];

  function dfs(node: TreeNode | null, path: number[], sum: number): void {
    if (!node) return;
    if (!node.left && !node.right && targetSum === sum + node.val) {
      paths.push([...path, node.val]);
      return;
    }
    dfs(node.left, [...path, node.val], sum + node.val);
    dfs(node.right, [...path, node.val], sum + node.val);
  }

  dfs(root, [], 0);
  return paths;
}
```

## Other's Solution

- Similar solutions.
