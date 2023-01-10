# [LeetCode] 82. Remove Duplicates from Sorted List II

## Problem

> Given the `head` of a sorted linked list, _delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list_. Return _the linked list **sorted** as well_.
> [[LeetCode] 82. Remove Duplicates from Sorted List II](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/description/?envType=study-plan&id=data-structure-ii)

## Solution

- From the head of the given linked list to the tail of the list, cut and re-connect `next` node with next unique node.
- In sorted list, unique node can be tell by the function named `isUniqueNode`.
- Also we can find the next unique node with the function named `findNextUniqueNode`.
- The only edge case is when the given node is not a unique node.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function deleteDuplicates(head: ListNode | null): ListNode | null {
  const filtered = isUniqueNode(head) ? head : findNextUniqueNode(head);
  let current = filtered;
  while (current) {
    current.next = findNextUniqueNode(current);
    current = current.next;
  }
  return filtered;
}

function findNextUniqueNode(node: ListNode | null): ListNode | null {
  if (!node) return null;
  if (isUniqueNode(node) && isUniqueNode(node.next)) return node.next;
  return findNextUniqueNode(node.next);
}

function isUniqueNode(node: ListNode | null): boolean {
  return !node || !node.next || node.val !== node.next.val;
}
```

## Other's Solution

- Other solutions have poor readability but using similar approach.
