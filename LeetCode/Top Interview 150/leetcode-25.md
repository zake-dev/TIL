# [[LeetCode] 25. Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group)

# Solution - TypeScript

```typescript
function reverseKGroup(head: ListNode | null, k: number): ListNode | null {
  if (head === null || head.next === null) return head;

  const length = lengthOf(head);
  if (k > length) return head;

  let previous: ListNode | null = null;
  let current = head;
  let next: ListNode | null = head.next;
  for (let i = 0; i < k; i++) {
    next = current.next;
    current.next = previous;
    previous = current;
    current = next;
  }

  if (current !== null) head.next = reverseKGroup(current, k);

  return previous;
}

function lengthOf(head: ListNode | null): number {
  let length = 0;
  while (head !== null) {
    head = head.next;
    length++;
  }
  return length;
}
```
