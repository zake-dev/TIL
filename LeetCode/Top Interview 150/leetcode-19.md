# [[LeetCode] 19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description)

# Solution - TypeScript

```typescript
function removeNthFromEnd(head: ListNode | null, n: number): ListNode | null {
  let nodeToRemove = null;
  let nodeToTail = null;

  for (let i = 0; i < n; i++) {
    nodeToTail = nodeToTail?.next ?? head;
  }

  while (nodeToTail.next !== null) {
    nodeToTail = nodeToTail.next;
    nodeToRemove = nodeToRemove?.next ?? head;
  }

  if (nodeToRemove === null) return head.next;
  nodeToRemove.next = nodeToRemove.next?.next ?? null;

  return head;
}
```
