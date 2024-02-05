# [[LeetCode] 146. LRU Cache](https://leetcode.com/problems/lru-cache/description)

# Solution - TypeScript

```typescript
class DoubleListNode {
  key: number;
  val: number;
  prev: DoubleListNode | null;
  next: DoubleListNode | null;

  constructor(key, val, prev = null, next = null) {
    this.key = key;
    this.val = val;
    this.prev = prev;
    this.next = next;
  }
}

class LRUCache {
  capacity: number;
  map = new Map<number, DoubleListNode>();
  head = new DoubleListNode(-1, -1);
  tail = new DoubleListNode(-1, -1);

  constructor(capacity: number) {
    this.capacity = capacity;
    this.head.next = this.tail;
    this.tail.prev = this.head;
  }

  get(key: number): number {
    if (!this.map.has(key)) return -1;

    const node = this.map.get(key);
    this.updatePriorities(node);
    return node.val;
  }

  put(key: number, value: number): void {
    if (this.map.has(key)) {
      const node = this.map.get(key);
      this.updatePriorities(node);
      node.val = value;
      return;
    }

    if (this.map.size === this.capacity) {
      const node = this.head.next;

      this.head.next = this.head.next.next;
      this.head.next.prev = this.head;
      this.map.delete(node.key);
    }

    const node = new DoubleListNode(key, value);
    node.next = this.tail;
    node.prev = this.tail.prev;

    this.tail.prev.next = node;
    this.tail.prev = node;
    this.map.set(key, node);
  }

  updatePriorities(node: DoubleListNode): void {
    node.prev.next = node.next;
    node.next.prev = node.prev;
    node.next = this.tail;
    node.prev = this.tail.prev;

    this.tail.prev.next = node;
    this.tail.prev = node;
  }
}
```
