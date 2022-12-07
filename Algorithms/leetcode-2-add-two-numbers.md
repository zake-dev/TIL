# [LeetCode] 2. Add Two Numbers

## Problem

> You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order**, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.
> You may assume the two numbers do not contain any leading zero, except the number 0 itself.
> [[LeetCode] 2. Add Two Numbers](https://leetcode.com/problems/add-two-numbers/description/)

## Solution

- Create a dummy head of new `ListNode` named `result`.
- Iterate while `l1` or `l2` is valid.
- Keep `carry` from last calculation.
- **Don't forget to append `ListNode(1)` if there is a carry after last iteration**.
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

function addTwoNumbers(
  l1: ListNode | null,
  l2: ListNode | null
): ListNode | null {
  const result = new ListNode(0);

  let current = result;
  let carry = 0;
  while (l1 || l2) {
    const sum = getOrElse(l1, 0) + getOrElse(l2, 0) + carry;
    carry = +(sum >= 10);
    current.next = new ListNode(sum % 10);
    current = current.next;
    if (l1) l1 = l1.next;
    if (l2) l2 = l2.next;
  }

  if (carry) current.next = new ListNode(1);
  return result.next;
}

function getOrElse(node: ListNode | null, defaultValue: number): number {
  if (!node) return defaultValue;
  return node.val;
}
```

## Other's Solution

- Recursive version is a bit more concise.
- Runtime Complexity: **O(n)**

```typescript
function addTwoNumbers(
  l1: ListNode | null,
  l2: ListNode | null,
  carryOver: number = 0
): ListNode | null {
  if (l1 === null && l2 === null) {
    return !carryOver ? null : new ListNode(carryOver);
  }

  const currentSum = (l1?.val || 0) + (l2?.val || 0) + carryOver;
  return new ListNode(
    currentSum % 10,
    addTwoNumbers(l1?.next || null, l2?.next || null, (currentSum / 10) >> 0)
  );
}
```
