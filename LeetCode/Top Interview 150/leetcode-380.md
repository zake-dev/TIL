# [[LeetCode] 380. Insert Delete GetRandom O(1)](https://leetcode.com/problems/insert-delete-getrandom-o1/description)

# Solution - TypeScript

```typescript
class RandomizedSet {
  map: Map<number, number>;
  keys: number[];

  constructor() {
    this.map = new Map<number, number>();
    this.keys = [];
  }

  insert(val: number): boolean {
    if (this.map.has(val)) return false;
    this.map.set(val, this.keys.length);
    this.keys.push(val);
    return true;
  }

  remove(val: number): boolean {
    if (!this.map.has(val)) return false;

    const indexToRemove = this.map.get(val);
    const lastKey = this.keys[this.keys.length - 1];
    this.map.set(lastKey, indexToRemove);
    this.keys[indexToRemove] = lastKey;
    this.keys.pop();
    this.map.delete(val);
    return true;
  }

  getRandom(): number {
    const random = Math.floor(Math.random() * this.keys.length);
    return this.keys[random];
  }
}
```
