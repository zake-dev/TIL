# [LeetCode] 105. Construct Binary Tree from Preorder and Inorder Traversal

## Problem

> Given two integer arrays `preorder` and `inorder` where `preorder` is the preorder traversal of a binary tree and `inorder` is the inorder traversal of the same tree, construct and return _the binary tree_.
> [[LeetCode] 105. Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/?envType=study-plan&id=data-structure-ii)

## Solution

- The first element of `preorder` is a `root` node of every subtree. Pop first element from `preorder` and create a `root` node with it.
- As the characteristics of inorder traversal, `inorder` array can be partitioned left nodes and right nodes by the index of `root` node. For example, if `root = 3` and `inorder = [9, 3, 15, 20, 7]`, we can say `leftNodes = [9]` and `rightNodes = [15, 20, 7]`.
- An empty `inorder` array means there is no subtree under this node.
- So we can recursively build tree.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function buildTree(preorder: number[], inorder: number[]): TreeNode | null {
  if (!inorder.length) return null;
  const root = new TreeNode(preorder.shift());
  const partition = inorder.indexOf(root.val);
  root.left = buildTree(preorder, inorder.slice(0, partition));
  root.right = buildTree(preorder, inorder.slice(partition + 1));
  return root;
}
```

## Other's Solution

- Recursive way is most efficient for this problem.
