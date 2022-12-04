# [LeetCode] 21. Merge Two Sorted Lists

## Problem

> You are given the heads of two sorted linked lists `list1` and `list2`.
> Merge the two lists in a one **sorted** list. The list should be made by splicing together the nodes of the first two lists.
> Return _the head of the merged linked list_.
> [[LeetCode] 21. Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/?envType=study-plan&id=data-structure-i)

## Solution

- Create new head of a linked list and track with `current` pointer.
- Take a node from `list1` or `list2` which is smaller than the other.
- Append the taken node to `current`, and move pointers forward.
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

function mergeTwoLists(
  list1: ListNode | null,
  list2: ListNode | null
): ListNode | null {
  const beforeHead = new ListNode();
  let current = beforeHead;
  while (list1 !== null || list2 !== null) {
    if (list1 === null) {
      current.next = list2;
      break;
    }
    if (list2 === null) {
      current.next = list1;
      break;
    }
    if (list1.val <= list2.val) {
      current.next = list1;
      current = current.next;
      list1 = list1.next;
    } else {
      current.next = list2;
      current = current.next;
      list2 = list2.next;
    }
  }
  return beforeHead.next;
}
```

## Other's Solution

- No difference with other solutions.
