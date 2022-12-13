# [LeetCode] 706. Design HashMap

## Problem

> Design a HashMap without using any built-in hash table libraries.
> Implement the `MyHashMap` class:
> `MyHashMap()` initializes the object with an empty map.
>
> - `void put(int key, int value)` inserts a `(key, value)` pair into the HashMap. If the key already exists in the map, update the corresponding `value`.
> - `int get(int key)` returns the `value` to which the specified `key` is mapped, or `-1` if this map contains no mapping for the `key`.
> - `void remove(key)` removes the `key` and its corresponding `value` if the map contains the mapping for the `key`.

> [[LeetCode] 706. Design HashMap](https://leetcode.com/problems/design-hashmap/?envType=study-plan&id=data-structure-ii)

## Solution

- Easy but not scalable solution.
- As the range of `key` is `0 <= value <= 10^6`, `key` can be stored in `array` without hashing.
- Create an empty `array` and implement methods.
- Runtime Complexity: **put: O(1), get: O(1), remove: O(1)**

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

- This problem requires the knowledge to implement hash map data structure with hash function.
- You have to hash the given `key` and handle collisions occurred on input.
- This guy suggests a simple hash function using 2 prime numbers, and keep `(key, value)` into _array of linked list_.
- Runtime Complexity **put: O(1), get: O(1), remove: O(1)**

```typescript
class MyListNode {
  key: number;
  value: number;
  next?: MyListNode;

  constructor(key, value, next) {
    this.key = key;
    this.value = value;
    this.next = next;
  }
}

class MyHashMap {
  #TABLE_SIZE: number = 19997;
  #HASH_PRIME: number = 12582917;
  #hashTable: MyListNode[];

  constructor() {
    this.#hashTable = new Array(this.#TABLE_SIZE);
  }
  hash(key) {
    return (key * this.#HASH_PRIME) % this.#TABLE_SIZE;
  }
  put(key, value) {
    this.remove(key);
    let hashed = this.hash(key);
    let node = new MyListNode(key, value, this.#hashTable[hashed]);
    this.#hashTable[hashed] = node;
  }
  get(key) {
    let hashed = this.hash(key);
    for (let node = this.#hashTable[hashed]; node; node = node.next)
      if (node.key === key) return node.value;
    return -1;
  }
  remove(key) {
    let hashed = this.hash(key);
    let node = this.#hashTable[hashed];

    if (!node) return;
    if (node.key === key) this.#hashTable[hashed] = node.next;
    else
      for (; node.next; node = node.next)
        if (node.next.key === key) {
          node.next = node.next.next;
          return;
        }
  }
}
```
