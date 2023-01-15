# [LeetCode] 450. Delete Node in a BST

## Problem

> Given a root node reference of a BST and a key, delete the node with the given key in the BST. Return _the **root node reference** (possibly updated) of the BST_.
> Basically, the deletion can be divided into two stages:
> Search for a node to remove.
> If the node is found, delete the node.
> [[LeetCode] 450. Delete Node in a BST](https://leetcode.com/problems/delete-node-in-a-bst/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Failed to find optimized solution for this.
- This approach deletes node in four steps.
  1. Find target node using DFS algorithm.
  2. Rebuild BST from the target node if it exists. Drop self but build BST from child nodes.
  3. To rebuild BST, extract values in child nodes using preorder traversing.
  4. Push all newly created `TreeNode` to `dummyRoot`(which will take every nodes at right side).
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function deleteNode(root: TreeNode | null, key: number): TreeNode | null {
  function dfs(node: TreeNode | null): TreeNode | null {
    if (!node) return null;
    if (node.val === key) return rebuildBST(node);
    node.left = dfs(node.left);
    node.right = dfs(node.right);
    return node;
  }

  return dfs(new TreeNode(NaN, null, root)).right;
}

function rebuildBST(node: TreeNode | null): TreeNode | null {
  if (!node.left && !node.right) return null;

  const dummyRoot = new TreeNode(-Infinity);
  const queue = preorder(node, []);
  while (queue.length) pushToBST(dummyRoot, queue.shift());

  return dummyRoot.right;
}

function preorder(node: TreeNode | null, result: number[]): number[] {
  if (!node) return result;
  if (node.left) result.push(node.left.val);
  if (node.right) result.push(node.right.val);
  preorder(node.left, result);
  preorder(node.right, result);
  return result;
}

function pushToBST(root: TreeNode | null, val: number): TreeNode | null {
  if (!root) return new TreeNode(val);
  if (root.val > val) root.left = pushToBST(root.left, val);
  if (root.val < val) root.right = pushToBST(root.right, val);
  return root;
}
```

## Other's Solution

- It is ensured by the definition of BST that all nodes in left sub tree of a `node` are smaller than all nodes in right sub tree.
- So we can move left subtree into right subtree of the deleted node.
- Time Complexity: **O(logn)**, Space Complexity: **O(1)**

```typescript
function deleteNode(root: TreeNode | null, key: number): TreeNode | null {
  if (!root) return null;
  if (root.val === key) return replaceSubTree(root);
  if (root.val < key) root.right = deleteNode(root.right, key);
  if (root.val > key) root.left = deleteNode(root.left, key);
  return root;
}

function replaceSubTree(root: TreeNode | null): TreeNode | null {
  if (!root.left) return root.right;
  if (!root.right) return root.left;
  return mergeBSTs(root.left, root.right);
}

function mergeBSTs(
  left: TreeNode | null,
  right: TreeNode | null
): TreeNode | null {
  if (!right.left) {
    right.left = left;
    return right;
  }
  mergeBSTs(left, right.left);
  return right;
}
```
