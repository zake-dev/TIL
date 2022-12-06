# [LeetCode] 232. Implement Queue using Stacks

## Problem

> Implement a first in first out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue (`push`, `peek`, `pop`, and `empty`).

> Implement the `MyQueue` class:
>
> - `void push(int x)` Pushes element x to the back of the queue.
> - `int pop()` Removes the element from the front of the queue and returns it.
> - `int peek()` Returns the element at the front of the queue.
> - `boolean empty()` Returns `true` if the queue is empty, `false` otherwise.
> - You must use only standard operations of a stack, which means only `push to top`, `peek/pop from top`, `size`, and `is empty` operations are valid.
> - Depending on your language, the stack may not be supported natively. You may simulate a stack using a list or deque (double-ended queue) as long as you use only a stack's standard operations.

> [[LeetCode] 232. Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/?envType=study-plan&id=data-structure-i)

## Solution

- As there is no `stack` implementation in Javascript/Typescript, I utilized `stack methods` to `StackUtil` first.
- In my opinion, speed of getting data is more important than putting it when it comes to web services.
- There are two stacks named `#stack` and `#queue` in `MyQueue` class. `#queue` will work as real queue implementation. `#stack` will only be used when the input comes in from the method `push`.
- Runtime Complexity: `push` **O(n)**, `pop/peek/empty` **O(1)**

```typescript
class StackUtil {
  static swapStacks<T>(from: T[], to: T[]): void {
    while (from.length) to.push(from.pop());
  }

  static peek<T>(stack: T[]): T {
    return stack[stack.length - 1];
  }
}

class MyQueue {
  #stack: number[];
  #queue: number[];

  constructor() {
    this.#stack = [];
    this.#queue = [];
  }

  push(x: number): void {
    StackUtil.swapStacks(this.#queue, this.#stack);
    this.#stack.push(x);
    StackUtil.swapStacks(this.#stack, this.#queue);
  }

  pop(): number {
    return this.#queue.pop();
  }

  peek(): number {
    return StackUtil.peek(this.#queue);
  }

  empty(): boolean {
    return this.#queue.length === 0;
  }
}
```

## Other's Solution

- Same solutions but different which method has slower process time, `push` or `pop/peek`.
