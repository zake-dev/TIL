# [LeetCode] 155. Min Stack

## Problem

> Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.
> Implement the `MinStack` class:
>
> - `MinStack()` initializes the stack object.
> - `void push(int val)` pushes the element `val` onto the stack.
> - `void pop()` removes the element on the top of the stack.
> - `int top()` gets the top element of the stack.
> - `int getMin()` retrieves the minimum element in the stack.
>
> You must implement a solution with `O(1)` time complexity for each function.
> [[LeetCode] 155. Min Stack](https://leetcode.com/problems/min-stack/description/?envType=study-plan&id=data-structure-ii)

## Solution

- To ensure all methods in `MinStack` run in `O(1)` time complexity, the key point is how to handle minimum element in the stack.
- First thought was that updating `min` value as a field whenever new `val` is pushed. However, this approach has a big problem with handling `pop`. If the popped element is a current `min` value, we should iterate over all stack to find the next `min`.
- That's why I used another stack named `mins`. This stack handles previous `min` values, and will be popped when minimum element is popped. You have to push current `min` into `mins` if the new `val` is smaller than current `min`.
- Time Complexity: **O(1)**, Space Complexity: **O(n)**

```typescript
class MinStack {
  values: number[];
  mins: number[];
  min: number;

  constructor() {
    this.values = [];
    this.mins = [];
    this.min = Infinity;
  }

  push(val: number): void {
    this.values.push(val);
    if (val <= this.min) {
      this.mins.push(this.min);
      this.min = val;
    }
  }

  pop(): void {
    const val = this.values.pop();
    if (val === this.min) {
      this.min = this.mins.pop();
    }
  }

  top(): number {
    return this.values[this.values.length - 1];
  }

  getMin(): number {
    return this.min;
  }
}
```

## Other's Solution

- Design stack node self. Keep minimum value on push.
- Way more cleaner.
- Time Complexity: **O(1)**, Space Complexity: **O(n)**

```typescript
class MinStack {
  topNode: StackNode | null;

  constructor() {
    this.topNode = null;
  }

  push(val: number): void {
    const min = this.topNode?.min ?? Infinity;
    this.topNode = new StackNode(val, Math.min(min, val), this.topNode);
  }

  pop(): void {
    this.topNode = this.topNode.previous;
  }

  top(): number {
    return this.topNode.val;
  }

  getMin(): number {
    return this.topNode.min;
  }
}

class StackNode {
  val: number;
  min: number;
  previous: StackNode | null;

  constructor(val: number, min: number, previous: StackNode | null) {
    this.val = val;
    this.min = min;
    this.previous = previous;
  }
}
```
