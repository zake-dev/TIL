# [LeetCode] 103. Binary Tree Zigzag Level Order Traversal

## Problem

> Given the `root` of a binary tree, return \_the zigzag level order traversal of its nodes' value_s. (i.e., from left to right, then right to left for the next level and alternate between).
> [[LeetCode] 103. Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Easiest approach, understandable, good readability, but not optimized.
- Find a level order of the given tree and reverse odd-indexed levels.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function zigzagLevelOrder(root: TreeNode | null): number[][] {
  function levelOrder(
    node: TreeNode | null,
    level: number,
    orders: number[][]
  ): number[][] {
    if (!node) return orders;
    if (!orders[level]) orders[level] = [];
    orders[level].push(node.val);
    levelOrder(node.left, level + 1, orders);
    levelOrder(node.right, level + 1, orders);
    return orders;
  }

  return levelOrder(root, 0, []).map((nodes, level) => {
    return level & 1 ? nodes.reverse() : nodes;
  });
}
```

## Other's Solution

- To solve this problem without reversing arrays, queue and loop are needed.
- Set flag named `isReversed` to check where to put elements from.
- This is optimized solution but hard to read I think.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function zigzagLevelOrder(root: TreeNode | null): number[][] {
  if (!root) return [];

  const result: number[][] = [];

  const queue: TreeNode[] = [root];
  let isReversed = false;
  while (queue.length) {
    const rowSize = queue.length;
    const row = new Array(rowSize);

    for (let i = 0; i < rowSize; i++) {
      const node = queue.shift();
      const index = isReversed ? rowSize - 1 - i : i;
      row[index] = node.val;

      if (node.left) queue.push(node.left);
      if (node.right) queue.push(node.right);
    }

    result.push(row);
    isReversed = !isReversed;
  }

  return result;
}
```
