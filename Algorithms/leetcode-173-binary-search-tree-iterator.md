# [LeetCode] 173. Binary Search Tree Iterator

## Problem

> Implement the `BSTIterator` class that represents an iterator over the in-order traversal of a binary search tree (BST):
>
> - `BSTIterator(TreeNode root)` Initializes an object of the `BSTIterator` class. The `root` of the BST is given as part of the constructor. The pointer should be initialized to a non-existent number smaller than any element in the BST.
>
> - `boolean hasNext()` Returns `true` if there exists a number in the traversal to the right of the pointer, otherwise returns false.
> - `int next()` Moves the pointer to the right, then returns the number at the pointer.
>
> Notice that by initializing the pointer to a non-existent smallest number, the first call to `next()` will return the smallest element in the BST.
> You may assume that `next()` calls will always be valid. That is, there will be at least a next number in the in-order traversal when `next()` is called.
> [[LeetCode] 173. Binary Search Tree Iterator](https://leetcode.com/problems/binary-search-tree-iterator/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Used generator function syntax to implement `BSTIterator` class.
- Keep next value of generator. We can check whether the iterator has next value or not with such variable.
- Time Complexity: **O(1)**, Space Complexity: **O(1)**

```typescript
class BSTIterator {
  inorderGenerator: Generator;
  nextValue: number | null;

  constructor(root: TreeNode | null) {
    this.inorderGenerator = this.#inorder(root);
    this.nextValue = this.inorderGenerator.next().value;
  }

  *#inorder(node: TreeNode | null) {
    if (!node) return null;
    yield* this.#inorder(node.left);
    yield node.val;
    yield* this.#inorder(node.right);
    return null;
  }

  next(): number {
    const result = this.nextValue;
    this.nextValue = this.inorderGenerator.next().value;
    return result;
  }

  hasNext(): boolean {
    return this.nextValue !== null;
  }
}
```

## Other's Solution

- We can also store inorder traversal as an array, and keep current index of the pointer.
- Time Complexity: **constructor = O(n), next, hasNext = O(1)**, Space Complexity: **O(n)**

```typescript
class BSTIterator {
  inorder: number[];
  index: number;

  constructor(root: TreeNode | null) {
    this.inorder = [];
    this.index = 0;
    this.traverseInorder(root);
  }

  traverseInorder(node: TreeNode | null): void {
    if (!node) return;
    this.traverseInorder(node.left);
    this.inorder.push(node.val);
    this.traverseInorder(node.right);
  }

  next(): number {
    return this.inorder[this.index++];
  }

  hasNext(): boolean {
    return this.index < this.inorder.length;
  }
}
```
