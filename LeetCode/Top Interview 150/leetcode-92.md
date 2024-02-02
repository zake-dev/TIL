# [[LeetCode] 92. Reverse Linked List II](https://leetcode.com/problems/reverse-linked-list-ii/description)

# Solution - TypeScript

```typescript
function reverseBetween(head: ListNode | null, left: number, right: number): ListNode | null {
  if (head === null || left === right) return head;

  const dummyHead = new ListNode(0, head);

  let previous = dummyHead;
  let current = head;
  let next = current.next;

  let joinFromLeft: ListNode | null;
  let joinToRight: ListNode | null;

  let index = 1;
  while (current !== null && index <= right) {
    next = current.next;
    if (index === left) {
      joinFromLeft = previous;
      joinToRight = current;
    }
    if (index >= left) current.next = previous;
    previous = current;
    current = next;
    index++;
  }

  joinFromLeft.next = previous;
  joinToRight.next = current;
  return dummyHead.next;

```
