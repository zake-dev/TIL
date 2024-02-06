# [[LeetCode] 106. Construct Binary Tree from Inorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/description)

# Solution - TypeScript

```typescript
function buildTree(inorder: number[], postorder: number[]): TreeNode | null {
  let [inIndex, postIndex] = [0, 0];

  function build(inVal?: number): TreeNode | null {
    let node: TreeNode | null = null;

    for (
      ;
      inIndex < inorder.length && postorder[postIndex] !== inVal;
      postIndex++
    ) {
      node = new TreeNode(inorder[inIndex], node);
      if (inorder[inIndex] !== postorder[postIndex])
        node.right = build(inorder[inIndex++]);
      else inIndex++;
    }

    return node;
  }

  return build();
}
```
