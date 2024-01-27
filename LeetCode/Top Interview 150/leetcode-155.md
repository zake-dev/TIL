# [[LeetCode] 155. Min Stack](https://leetcode.com/problems/min-stack/description)

# Solution - TypeScript

```typescript
class StackNode {
  val: number;
  min: number;

  constructor(val: number, min: number) {
    this.val = val;
    this.min = min;
  }
}

class MinStack {
  stack: StackNode[];
  min: number;

  constructor() {
    this.stack = [];
    this.min = Infinity;
  }

  push(val: number): void {
    this.stack.push(new StackNode(val, this.min));
    this.min = Math.min(this.min, val);
  }

  pop(): void {
    const node = this.stack.pop();
    this.min = node.min;
  }

  top(): number {
    return this.stack[this.stack.length - 1].val;
  }

  getMin(): number {
    return this.min;
  }
}
```
