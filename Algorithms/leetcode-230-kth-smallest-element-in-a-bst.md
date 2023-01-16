# [LeetCode] 230. Kth Smallest Element in a BST

## Problem

> Given the `root` of a binary search tree, and an integer `k`, return _the `kth` smallest value (**1-indexed**) of all the values of the nodes in the tree_.
> [[LeetCode] 230. Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/?envType=study-plan&id=data-structure-ii)

## Solution

- Inorder traversal of a BST represents a sorted values in a BST by non-descending order.
- Find inorder traversal of a BST until it includes `k` elements.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function kthSmallest(root: TreeNode | null, k: number): number {
  function inorder(node: TreeNode | null, result: number[]): number[] {
    if (!node || result.length === k) return result;
    inorder(node.left, result);
    result.push(node.val);
    inorder(node.right, result);
    return result;
  }

  return inorder(root, [])[k - 1];
}
```

## Other's Solution

- Other solution also uses DFS algorithm.
