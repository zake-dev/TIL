# [LeetCode] 25. Reverse Nodes in k-Group

## Problem

> Given the `head` of a linked list, reverse the nodes of the list `k` at a time, and return _the modified list_.
> `k` is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of `k` then left-out nodes, in the end, should remain as it is.
> You may not alter the values in the list's nodes, only nodes themselves may be changed.
> [[LeetCode] 25. Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Using two recursive functions to solve. Iterate over the given linked list, reverse a sublist in k-group.
- `canReverse(node: ListNode | null, k: number): boolean` checks if the remaining list has enough length of `k`. If not, it will end the recursion with non-reversed remaining nodes.
- `reverseSublist(node: ListNode | null, k: number): ListNode[]` reverses nodes using recursion. It will stack function calls until the last node of a sublist, then will return _`tail` and `tailNext` which indicates very next head node of sublists_ as an array.
- Below solution is rewritten by me to improve readability.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function reorderList(head: ListNode | null): void {
  if (!head || !head.next) return;

  const [firstHalf, secondHalf] = splitList(head);
  const reversedHalf = reverseList(secondHalf);
  mergeList(firstHalf, reversedHalf);
}

function splitList(head: ListNode | null): ListNode[] {
  let [slow, fast] = [head, head];
  while (fast && fast.next) {
    slow = slow.next;
    fast = fast.next.next;
  }
  const middle = slow.next;
  slow.next = null;
  return [head, middle];
}

function reverseList(node: ListNode | null): ListNode | null {
  if (!node || !node.next) return node;
  const tail = reverseList(node.next);
  node.next.next = node;
  node.next = null;
  return tail;
}

function mergeList(a: ListNode | null, b: ListNode | null): void {
  if (!a || !b) return;
  const [c, d] = [a.next, b.next];
  [a.next, b.next] = [b, c];
  mergeList(c, d);
}
```
