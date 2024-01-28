# [[LeetCode] 21. Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/description)

# Solution - TypeScript

```typescript
function mergeTwoLists(
  list1: ListNode | null,
  list2: ListNode | null
): ListNode | null {
  const dummyHead = new ListNode();

  let current = dummyHead;
  while (list1 || list2) {
    if (list1 === null) {
      current.next = list2;
      break;
    } else if (list2 === null) {
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

  return dummyHead.next;
}
```
