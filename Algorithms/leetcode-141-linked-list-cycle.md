# [LeetCode] 141. Linked List Cycle

## Problem

> Given `head`, the head of a linked list, determine if the linked list has a cycle in it.
> There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to. **Note that** `pos` **is not passed as a parameter.**
> Return `true` _if there is a cycle in the linked list_. Otherwise, return `false`.
> [[LeetCode] 141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/?envType=study-plan&id=data-structure-i)

## Solution

- Use `Floyd's Cycle Detection Algorithm`.
- There are two pointers named `slow pointer` and `fast pointer`.
- `slow pointer` moves just 1 step for each. However, 'fast pointer` moves 2 steps for every iteration.
- If there is a cycle inside the given linked list, `slow pointer` and `fast pointer` will be same at some time.
- Otherwise, `fast pointer` will reach to the end of the linked list.
- Runtime Complexity: **O(n)**

```typescript
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     val: number
 *     next: ListNode | null
 *     constructor(val?: number, next?: ListNode | null) {
 *         this.val = (val===undefined ? 0 : val)
 *         this.next = (next===undefined ? null : next)
 *     }
 * }
 */

function hasCycle(head: ListNode | null): boolean {
  let slowPointer = head?.next;
  let fastPointer = head?.next?.next ?? null;
  while (fastPointer !== null) {
    if (slowPointer === fastPointer) return true;
    slowPointer = slowPointer.next;
    fastPointer = fastPointer.next?.next ?? null;
  }
  return false;
}
```

## Other's Solution

- Another intersting approach solves the problem by replacing the original values with `X`.
- If there is a cycle inside the linked list, the `pointer` will meet `ListNode` _which has a value of `X`_.
- However, this would be hard to be implemented using `typescript` as it replaces value of the node with _non-number type_.
- Runtime Complexity: **O(n)**

```javascript
var hasCycle = function (head) {
  let start = new ListNode(head);
  while (head) {
    if (head.val === "X") {
      return true;
    }
    head.val = "X";
    head = head.next;
  }
  return false;
};
```
