# [[LeetCode] 105. Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal)

# Solution - TypeScript

```typescript
function buildTree(preorder: number[], inorder: number[]): TreeNode | null {
  let root = null;
  let top = null;
  let pop = null;
  let i = 0;
  for (const val of preorder) {
    const node = new TreeNode(val);

    if (pop !== null) {
      pop.right = node;
      pop = null;
    } else if (top !== null) {
      top.left = node;
    } else {
      root = node;
    }

    node.right = top;
    top = node;
    while (top !== null && top.val === inorder[i]) {
      pop = top;
      top = pop.right;
      pop.right = null;
      i++;
    }
  }
  return root;
}
```
