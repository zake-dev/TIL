# [[LeetCode] 141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/description)

# Solution - TypeScript

```typescript
function hasCycle(head: ListNode | null): boolean {
  let [slow, fast] = [head, head];
  while (fast && fast.next) {
    slow = slow.next;
    fast = fast.next.next;
    if (slow === fast) return true;
  }
  return false;
}
```
