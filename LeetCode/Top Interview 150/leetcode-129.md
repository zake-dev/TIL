# [[LeetCode] 129. Sum root to Leaf Numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers/description)

# Solution - TypeScript

```typescript
function sumNumbers(root: TreeNode | null, sum: number = 0): number {
  if (root === null) return 0;
  if (root.left === null && root.right === null) return sum * 10 + root.val;
  return (
    sumNumbers(root.left, sum * 10 + root.val) +
    sumNumbers(root.right, sum * 10 + root.val)
  );
}
```
