# [[LeetCode] 61. Rotate List](https://leetcode.com/problems/rotate-list/description)

# Solution - TypeScript

```typescript
function rotateRight(head: ListNode | null, k: number): ListNode | null {
  const rotate = k % lengthOf(head);
  if (head === null || head.next === null || rotate === 0) return head;

  let tail = null;
  let newHeadPrevious = null;
  for (let i = 0; i < rotate; i++) {
    tail = tail?.next ?? head;
  }

  while (tail.next !== null) {
    tail = tail.next;
    newHeadPrevious = newHeadPrevious?.next ?? head;
  }

  if (newHeadPrevious === null) return head;
  const newHead = newHeadPrevious.next;
  newHeadPrevious.next = null;
  tail.next = head;

  return newHead;
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
