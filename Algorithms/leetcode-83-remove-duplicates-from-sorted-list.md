# [LeetCode] 83. Remove Duplicates from Sorted List

## Problem

> Given the `head` of a sorted linked list, _delete all duplicates such that each element appears only once_. Return _the linked list **sorted** as well_.
> [[LeetCode] 1. Two Sum](https://leetcode.com/problems/two-sum/?envType=study-plan&id=data-structure-i)

## Solution

- Use inline-recursive function to find next unique node.
- Connect `current` node to the next unique node found with the function.
- Keep removing duplicates until the end.
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

function deleteDuplicates(head: ListNode | null): ListNode | null {
  let current = head;
  while (current !== null) {
    current.next = (function findNextUniqueNode(
      next: ListNode | null,
      duplicate: number
    ) {
      if (next === null || next?.val !== duplicate) return next;
      return findNextUniqueNode(next.next, next.val);
    })(current, current.val);
    current = current.next;
  }
  return head;
}
```

## Other's Solution

- This function works same way but has more readability than mine.
- It looks way clear. :)
- Runtime Complexity: **O(n)**

```typescript
function deleteDuplicates(head: ListNode | null): ListNode | null {
  if (head === null) return head;
  let node = head;
  while (node && node.next) {
    if (node.next.val === node.val) {
      node.next = node.next.next;
    } else {
      node = node.next;
    }
  }
  return head;
}
```
