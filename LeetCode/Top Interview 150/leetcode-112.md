# [[LeetCode] 112. Path Sum](https://leetcode.com/problems/path-sum/description)

# Solution - TypeScript

```typescript
function hasPathSum(
  root: TreeNode | null,
  targetSum: number,
  sum: number = 0
): boolean {
  if (root === null) return false;
  if (root.left === null && root.right === null && targetSum === sum + root.val)
    return true;
  return (
    hasPathSum(root.left, targetSum, sum + root.val) ||
    hasPathSum(root.right, targetSum, sum + root.val)
  );
}
```
