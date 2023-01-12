# [LeetCode] 143. Reorder List

## Problem

> You are given the head of a singly linked-list. The list can be represented as:
> `L0 → L1 → … → Ln - 1 → Ln`
> Reorder the list to be on the following form:
> `L0 → Ln → L1 → Ln - 1 → L2 → Ln - 2 → …`
> You may not modify the values in the list's nodes. Only nodes themselves may be changed.
> [[LeetCode] 143. Reorder List](https://leetcode.com/problems/reorder-list/?envType=study-plan&id=data-structure-ii)

## Solution

- Not an optimized solution but easy to understand.
- First, put all nodes in the given list into a `stack`.
- Set two pointers named `begin` and `end` which moves from left-most to right-most and vice versa.
- Connect each nodes to appropriate nodes.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function reorderList(head: ListNode | null): void {
  const stack = pushToStack(head);
  let [begin, end] = [head, stack.pop()];
  while (begin !== end && begin.next !== end) {
    [begin.next, end.next] = [end, begin.next];
    [begin, end] = [end.next, stack.pop()];
  }
  end.next = null;
}

function pushToStack(node: ListNode | null): ListNode[] {
  const stack: ListNode[] = [];
  let current = node;
  while (current) {
    stack.push(current);
    current = current.next;
  }
  return stack;
}
```

## Other's Solution

- Brilliant, understandable solution using smaller functions.
- Basic idea of this solution is splitting the given list as two sublist at the middle, then reverse the second list.
- Take nodes from those two refined lists one by one and merge those into one.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function reorderList(head: ListNode | null): void {
  if (!head || !head.next) return head;

  const [firstHalf, secondHalf] = splitList(head);
  const reversedHalf = reverseList(secondHalf);
  mergeList(firstHalf, reversedHalf);
}

function splitList(head: ListNod | null): ListNode[] {
  let [slow, fast] = [head, head];
  while (fast && fast.next) {
    slow = slow.next;
    fast = fast.next.next;
  }
  const middle = slow.next;
  slow.next = null;
  return middle;
}

function reverseList(node: ListNode | null): ListNode | null {
  if (!node.next) return node;
  const tail = reverseList(node.next);
  tail.next.next = node;
  node.next = null;
  return tail;
}

function mergeList(a: ListNode | null, b: ListNode | null): void {
  const [c, d] = [a.next, b.next];
  [a.next, b.next] = [b, c];
  mergeList(c, d);
}
```
