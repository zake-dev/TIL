# [LeetCode] 160. Intersection of Two Linked Lists

## Problem

> Given the heads of two singly linked-lists `headA` and `headB`, return _the node at which the two lists intersect_. If the two linked lists have no intersection at all, return `null`.
> **Note** that the linked lists must **retain their original structure** after the function returns.
> [[LeetCode] 160. Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/description/)

## Solution

- Register all nodes following by `headA` into a hash set.
- While iterating over following nodes by `headB`, if the node exists in the hash set, return the node.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function getIntersectionNode(
  headA: ListNode | null,
  headB: ListNode | null
): ListNode | null {
  const hashSet = new Set();
  while (headA) {
    hashSet.add(headA);
    headA = headA.next;
  }
  while (headB) {
    if (hashSet.has(headB)) return headB;
    headB = headB.next;
  }
  return null;
}
```

## Other's Solution

- Great, intuitive solution. Simple lines of code but covers all cases.
- If the length of list `A` and list `B` is same, it will directly find intersected node.
- If the length of list `A` and list `B` is different, iteration will be continued until `n`(which is lowest common multiple of length `A` and length `B`) times. Two pointers will meet at intersected node after iteration.
- However, if there is no intersection, loop will end up with `null` pointer.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function getIntersectionNode(
  headA: ListNode | null,
  headB: ListNode | null
): ListNode | null {
  let [a, b] = [headA, headB];
  while (a !== b) {
    a = a ? a.next : headB;
    b = b ? b.next : headA;
  }
  return a;
}
```
