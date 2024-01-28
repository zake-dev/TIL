# [[LeetCode] 2. Add Two Numbers](https://leetcode.com/problems/add-two-numbers/description)

# Solution - TypeScript

```typescript
function addTwoNumbers(
  l1: ListNode | null,
  l2: ListNode | null
): ListNode | null {
  const head = new ListNode();

  let current = head;
  let carry = 0;
  while (carry || l1 || l2) {
    const val1 = l1?.val ?? 0;
    const val2 = l2?.val ?? 0;
    const sum = val1 + val2 + carry;
    current.val = sum % 10;
    carry = sum >= 10 ? 1 : 0;

    l1 = l1?.next;
    l2 = l2?.next;
    if (carry || l1 || l2) current.next = new ListNode();
    current = current.next;
  }

  return head;
}
```
