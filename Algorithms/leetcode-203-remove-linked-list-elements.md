# [LeetCode] 203. Remove Linked List Elements

## Problem

> Given the `head` of a linked list and an integer `val`, remove all the nodes of the linked list that has `Node.val == val`, and return _the new head_.
> [[LeetCode] 203. Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/)

## Solution

- Create `new head` of a linked list.
- Append new `ListNode` if the `val` of the node is not a `target`.
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

function removeElements(head: ListNode | null, val: number): ListNode | null {
  const filteredHead = new ListNode();
  let filteredCurrent = filteredHead;
  for (let current = head; current !== null; current = current.next) {
    if (current.val !== val) {
      filteredCurrent.next = new ListNode(current.val);
      filteredCurrent = filteredCurrent.next;
    }
  }
  return filteredHead.next;
}
```

## Other's Solution

- No difference with other solutions.
