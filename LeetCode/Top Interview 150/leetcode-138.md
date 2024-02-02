# [[LeetCode] 138. Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/description)

# Solution - TypeScript

```typescript
function copyRandomList(head: Node | null): Node | null {
  if (head === null) return null;

  const cloneMap = new Map<Node, Node>();
  let current = head;
  while (current !== null) {
    cloneMap.set(current, new Node(current.val));
    current = current.next;
  }

  current = head;
  while (current !== null) {
    const cloneNode = cloneMap.get(current);
    cloneNode.random = cloneMap.get(current.random) ?? null;
    cloneNode.next = cloneMap.get(current.next) ?? null;
    current = current.next;
  }

  return cloneMap.get(head);
}
```
