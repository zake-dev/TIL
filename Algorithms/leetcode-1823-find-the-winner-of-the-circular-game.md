# [LeetCode] 1823. Find the Winner of the Circular Game

## Problem

> There are `n` friends that are playing a game. The friends are sitting in a circle and are numbered from `1` to `n` in clockwise order. More formally, moving clockwise from the `ith` friend brings you to the `(i+1)th` friend for `1 <= i < n`, and moving clockwise from the `nth` friend brings you to the `1st` friend.
> The rules of the game are as follows:
> **Start** at the `1st` friend.
> Count the next `k` friends in the clockwise direction **including** the friend you started at. The counting wraps around the circle and may count some friends more than once.
> The last friend you counted leaves the circle and loses the game.
> If there is still more than one friend in the circle, go back to step `2` starting from the friend **immediately clockwise** of the friend who just lost and repeat.
> Else, the last friend in the circle wins the game.
> Given the number of friends, `n`, and an integer `k`, return the winner of the game.
> [[LeetCode] 1823. Find the Winner of the Circular Game](https://leetcode.com/problems/find-the-winner-of-the-circular-game/description/)

## Solution

- Define `CircularQueue` to simulate the game.
  - `CircularQueue` has a `head: QueueNode | null` which indicates current head of the queue, and `size: number` the size of the queue.
  - `static createRangeQueue(start: number, end: number): CircularQueue` generates circular queue that can be used for the game.
  - `shift(n: number): void` moves `head` to `n` steps clockwise.
  - `unshift(n: number): void` moves `head` to `n` steps anti-clockwise.
  - `drop(): void` removes current `head` node from the queue, and set `head` as previous node.
- With `CircularQueue` class, generate a game. Set initial `head` to the end of the queue using `unshift` method.
- Move `k` steps clockwise using `shift` method, and drop the node from queue.
- Repeat until the size of the queue reaches to `1`.
- Return _the remaining node in the queue_.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function findTheWinner(n: number, k: number): number {
  const circularQueue = CircularQueue.createRangeQueue(1, n);

  circularQueue.unshift(1);
  while (circularQueue.size > 1) {
    circularQueue.shift(k);
    circularQueue.drop();
  }

  return circularQueue.head.val;
}

class CircularQueue {
  head: QueueNode;
  size: number;

  constructor(node: QueueNode) {
    this.head = node;
    this.length = 1;
  }

  static createRangeQueue(start: number, end: number): CircularQueue {
    const queue = new this(new QueueNode(start));

    let current = queue.head;
    for (let i = start + 1; i <= end; i++) {
      current.next = new QueueNode(i);
      current.next.previous = current;
      current = current.next;
      queue.length++;
    }
    current.next = queue.head;
    queue.head.previous = current;

    return queue;
  }

  shift(n: number): void {
    for (let i = 0; i < n; i++) this.head = this.head.next;
  }

  unshift(n: number): void {
    for (let i = 0; i < n; i++) this.head = this.head.previous;
  }

  drop(): void {
    const previous = this.head.previous;
    const next = this.head.next;
    previous.next = next;
    next.previous = previous;
    this.head = previous;
    this.length--;
  }
}

class QueueNode {
  val: number;
  next: QueueNode | null;
  previous: QueueNode | null;

  constructor(
    val: number,
    next?: QueueNode | null,
    previous?: QueueNode | null
  ) {
    this.val = val;
    this.next = next ?? null;
    this.previous = previous ?? null;
  }
}
```

## Other's Solution

- However, this problem can be solved with arithmetic index calculation.
- Find next index with modular operation, splice the array.
- Repeat until the length of `friends` reaches to `1`.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function findTheWinner(n: number, k: number): number {
  const friends: number[] = Array.from({ length: n }, (_, i) => i + 1);

  let cursor = 0;
  while (friends.length > 1) {
    cursor = (cursor + k - 1) % friends.length;
    const next = cursor === friends.length - 1 ? 0 : cursor;
    friends.splice(cursor, 1);
    cursor = next;
  }

  return friends[0];
}
```
