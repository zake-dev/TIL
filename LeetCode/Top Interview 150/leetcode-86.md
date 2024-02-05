# [[LeetCode] 86. Partition List](https://leetcode.com/problems/partition-list/description)

# Solution - TypeScript

```typescript
function partition(head: ListNode | null, x: number): ListNode | null {
  let leftDummyHead = new ListNode();
  let leftCurrent = leftDummyHead;
  let rightDummyHead = new ListNode();
  let rightCurrent = rightDummyHead;

  while (head !== null) {
    if (head.val < x) {
      leftCurrent.next = head;
      leftCurrent = leftCurrent.next;
    } else {
      rightCurrent.next = head;
      rightCurrent = rightCurrent.next;
    }
    head = head.next;
  }

  leftCurrent.next = rightDummyHead.next;
  rightCurrent.next = null;
  return leftDummyHead.next;
}
```
