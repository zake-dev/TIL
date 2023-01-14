# [LeetCode] 108. Convert Sorted Array to Binary Search Tree

## Problem

> Given an integer array `nums` where the elements are sorted in **ascending order**, convert _it to a height-balanced binary search tree_.
> [[LeetCode] 108. Convert Sorted Array to Binary Search Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/description/?envType=study-plan&id=data-structure-ii)

## Solution

- To build a height-balanced binary search tree from the sorted array, `root` node of each subtree is a middle indexed element in the array.
- Find `root` node, then append left subtree and right subtree recursively.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function sortedArrayToBST(nums: number[]): TreeNode | null {
  if (!nums.length) return null;
  const mid = ~~(nums.length / 2);
  const root = new TreeNode(nums[mid]);
  root.left = sortedArrayToBST(nums.slice(0, mid));
  root.right = sortedArrayToBST(nums.slice(mid + 1));
  return root;
}
```

## Other's Solution

- Also this approach can be optimized regarding to space complexity.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function sortedArrayToBST(nums: number[]): TreeNode | null {
  function buildBST(left: number, right: number): TreeNode | null {
    if (left > right) return null;
    const mid = ~~((left + right) / 2);
    const root = new TreeNode(nums[mid]);
    root.left = buildBST(left, mid - 1);
    root.right = buildBST(mid + 1, right);
    return root;
  }

  return buildBST(0, nums.length - 1);
}
```
