# [[LeetCode] 100. Same Tree](https://leetcode.com/problems/same-tree/description)

# Solution - TypeScript

```typescript
function isSameTree(p: TreeNode | null, q: TreeNode | null): boolean {
  if (p === null && q === null) return true;
  if (p?.val !== q?.val) return false;
  return isSameTree(p?.left, q?.left) && isSameTree(p?.right, q?.right);
}
```
