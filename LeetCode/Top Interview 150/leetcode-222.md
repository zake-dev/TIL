# [[LeetCode] 222. Count Complete Tree Nodes](https://leetcode.com/problems/count-complete-tree-nodes/description)

# Solution - TypeScript

```typescript
function countNodes(root: TreeNode | null, level: number = 0): number {
  if (root === null) return 0;

  const queue = [root];

  let count = 0;
  while (queue.length > 0) {
    let node = queue.pop();
    count++;
    if (node.left !== null) queue.push(node.left);
    if (node.right !== null) queue.push(node.right);
  }

  return count;
}
```
