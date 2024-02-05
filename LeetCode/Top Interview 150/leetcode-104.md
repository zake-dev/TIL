# [[LeetCode] 104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/description)

# Solution - TypeScript

```typescript
function maxDepth(root: TreeNode | null, depth: number = 1): number {
  if (root === null) return depth - 1;
  return Math.max(
    maxDepth(root.left, depth + 1),
    maxDepth(root.right, depth + 1)
  );
}
```
