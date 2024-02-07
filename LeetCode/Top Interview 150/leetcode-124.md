# [[LeetCode] 124. Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/description)

# Solution - TypeScript

```typescript
function maxPathSum(root: TreeNode | null): number {
  let maxSum = root.val;

  function dfs(node: TreeNode | null): number {
    if (node === null) return 0;

    const leftMax = Math.max(0, dfs(node.left));
    const rightMax = Math.max(0, dfs(node.right));

    const sum = node.val + leftMax + rightMax;
    maxSum = Math.max(maxSum, sum);

    return node.val + Math.max(leftMax, rightMax);
  }
  dfs(root);

  return maxSum;
}
```
