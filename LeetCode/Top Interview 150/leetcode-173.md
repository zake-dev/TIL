# [[LeetCode] 173. Binary Search Tree Iterator](https://leetcode.com/problems/binary-search-tree-iterator/description)

# Solution - TypeScript

```typescript
class BSTIterator {
  stack: (TreeNode | null)[];

  constructor(root: TreeNode | null) {
    this.stack = [];

    let node = root;
    while (node !== null) {
      this.stack.push(node);
      node = node.left;
    }
  }

  next(): number {
    const top = this.stack.pop();
    let node = top.right;

    while (node !== null) {
      this.stack.push(node);
      node = node.left;
    }

    return top.val;
  }

  hasNext(): boolean {
    return this.stack.length > 0;
  }
}
```
