# [LeetCode] 589. N-ary Tree Preorder Traversal

## Problem

> Given the `root` of an n-ary tree, return the preorder traversal of its nodes' values.
> Nary-Tree input serialization is represented in their level order traversal. Each group of children is separated by the null value (See examples)
> [[LeetCode] 589. N-ary Tree Preorder Traversal](https://leetcode.com/problems/n-ary-tree-preorder-traversal/description/?envType=study-plan&id=programming-skills-i)

## Solution

- Traverse tree with recursion.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function preorder(root: Node | null): number[] {
  function traverse(node: Node | null, preorder: number[]): number[] {
    if (!node) return preorder;
    preorder.push(node.val);
    node.children.forEach((child) => traverse(child, preorder));
    return preorder;
  }

  return traverse(root, []);
}
```

## Other's Solution

- No other intuitive solution exists.
