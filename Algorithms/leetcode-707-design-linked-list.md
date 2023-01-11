# [LeetCode] 707. Design Linked List

## Problem

> Design your implementation of the linked list. You can choose to use a singly or doubly linked list.
> A node in a singly linked list should have two attributes: `val` and `next`. `val` is the value of the current node, and `next` is a pointer/reference to the next node.
> If you want to use the doubly linked list, you will need one more attribute `prev` to indicate the previous node in the linked list. Assume all nodes in the linked list are 0-indexed.
> Implement the `MyLinkedList` class:
>
> - `MyLinkedList()` Initializes the `MyLinkedList` object.
> - `int get(int index)` Get the value of the `indexth` node in the linked list. If the index is invalid, return `-1`.
> - `void addAtHead(int val)` Add a node of value `val` before the first element of the linked list. After the insertion, the new node will be the first node of the linked list.
> - `void addAtTail(int val)` Append a node of value val as the last element of the linked list.
> - `void addAtIndex(int index, int val)` Add a node of value `val` before the `indexth` node in the linked list. If `index` equals the length of the linked list, the node will be appended to the end of the linked list. If `index` is greater than the length, the node **will not be inserted**.
> - `void deleteAtIndex(int index)` Delete the `indexth` node in the linked list, if the index is valid.
>
> [[LeetCode] 707. Design Linked List](https://leetcode.com/problems/design-linked-list/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Store `head` of the list, and current `length` of the list.
- Implement listed functions. Extract common logic from those to `findNodeByIndex(index: number): ListNode` which is a private method.
- Time Complexity:
  - `constructor()`: **O(1)**
  - `get(index: number): number`: **O(n)**
  - `addAtHead(val: number): void`: **O(1)**
  - `addAtTail(val: number): void`: **O(1)**
  - `addAtIndex(val: number): void`: **O(n)**
  - `deleteAtIndex(index: number): void`: **O(n)**
- Space Complexity: **O(1) ~ O(n)**

```typescript
class MyHashMap {
  #map: number[];

  constructor() {
    this.#map = [];
  }

  put(key: number, value: number): void {
    this.#map[key] = value;
  }

  get(key: number): number {
    return this.#map[key] ?? -1;
  }

  remove(key: number): void {
    delete this.#map[key];
  }
}
```

## Other's Solution

- This is a design and implementation problem. Similar logic applied for other solutions.
