# [LeetCode] 24. Swap Nodes in Pairs

## Problem

> Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)
> [[LeetCode] 24. Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Stack the function call recursively until it reaches to the end. If the length of the give linked list is odd, simply return last node, otherwise swap it.
- Swap two adjacent nodes and return node which is positioned at the front of other.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function swapPairs(head: ListNode | null): ListNode | null {
  if (!head || !head.next) return head;

  const nextPair = swapPairs(head.next.next);
  const next = head.next;
  head.next = nextPair;
  next.next = head;

  return next;
}
```

## Other's Solution

- Using two pointers and iterative way.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function swapPairs(head: ListNode | null): ListNode | null {
  const dummy = new ListNode(null, head);
  let [previous, current] = [dummy, head];
  while (current && current.next) {
    previous.next = current.next;
    current.next = current.next.next;
    previous.next.next = current;
    [previous, current] = [current, current.next];
  }
  return dummy.next;
}
```
