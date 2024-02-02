# [[LeetCode] 82. Remove Duplicates from Sorted List II](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii)

# Solution - TypeScript

```typescript
function deleteDuplicates(head: ListNode | null): ListNode | null {
  const dummyHead = new ListNode(Infinity, head);

  let previous = dummyHead;
  let current = head;
  while (current !== null && current.next !== null) {
    if (current.val === current.next.val) {
      previous.next = findNextUnique(current.next.next, current.val);
      current = previous.next;
      continue;
    }

    previous = current;
    current = current.next;
  }

  return dummyHead.next;
}

function findNextUnique(
  node: ListNode | null,
  duplicate: number
): ListNode | null {
  if (node === null || node.val !== duplicate) return node;
  return findNextUnique(node.next, duplicate);
}
```
