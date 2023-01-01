# [LeetCode] 237. Delete Node in a Linked List

## Problem

> There is a singly-linked list `head` and we want to delete a node `node` in it.
> You are given the node to be deleted `node`. You will **not be given access** to the first node of `head`.
> All the values of the linked list are **unique**, and it is guaranteed that the given node `node` is not the last node in the linked list.
> Delete the given node. Note that by deleting the node, we do not mean removing it from memory. We mean:
>
> - The value of the given node should not exist in the linked list.
> - The number of nodes in the linked list should decrease by one.
> - All the values before `node` should be in the same order.
> - All the values after `node` should be in the same order.
>
> [[LeetCode] 237. Delete Node in a Linked List](https://leetcode.com/problems/delete-node-in-a-linked-list/description/)

## Solution

- We cannot access `head` of the given linked list, so we cannot directly drop node from the list.
- However, the problem says deleting the node does not only mean dropping a node directly. We can copy and overwrite `node.val` to `node.next.val` from the given node `node` to `tail`.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function deleteNode(node: ListNode | null): void {
  while (node.next.next) {
    node.val = node.next.val;
    node = node.next;
  }
  node.val = node.next.val;
  node.next = null;
}
```

## Other's Solution

- Actually, I don't have to copy all of the rest nodes. What I needed is just copy of next value and next node pointer only. :(
- Runtime Complexity: **O(1)**, Space Complexity: **O(1)**

```typescript
function deleteNode(node: ListNode | null): void {
  node.val = node.next.val;
  node.next = node.next.next;
}
```
