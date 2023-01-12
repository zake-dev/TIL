# [LeetCode] 206. Reverse Linked List

## Problem

> Given the `head` of a singly linked list, reverse the list, and return _the reversed list_.
> [[LeetCode] 206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)

## Solution

- It was too hard to imagine how the computer operates recursive function without using a paper and a pen. :(
- Basically, the function should find the `last node` of the given linked list.
- After then, reverse the direction of the singly-linked list.
- Runtime Complexity: **O(n)**

```typescript
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     val: number
 *     next: ListNode | null
 *     constructor(val?: number, next?: ListNode | null) {
 *         this.val = (val===undefined ? 0 : val)
 *         this.next = (next===undefined ? null : next)
 *     }
 * }
 */

function reverseList(head: ListNode | null): ListNode | null {
  const recursiveReverse = (
    current: ListNode | null,
    prev: ListNode | null
  ) => {
    if (current === null) return prev;
    const tail = recursiveReverse(current.next, current);
    current.next = prev;
    return tail;
  };

  return recursiveReverse(head, null);
}
```

## Other's Solution

- Another impressive solution using recursion!
- It also finds `tail` node first, but does not track `prev` node.
- Instead of that, the function reverses the direction from the call stack which uses a `head` node is equivalent to `prev`.
- Runtime Complexity: **O(n)**

```typescript
function reverseList(head: ListNode | null) {
  if (head == null || head.next == null) return head;
  const tail = reverseList(head.next);
  head.next.next = head;
  head.next = null;
  return tail;
}
```
