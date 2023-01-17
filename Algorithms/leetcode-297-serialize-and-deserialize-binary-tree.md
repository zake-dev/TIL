# [LeetCode] 297. Serialize and Deserialize Binary Tree

## Problem

> Serialization is the process of converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.
> Design an algorithm to serialize and deserialize a binary tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure.
> [[LeetCode] 297. Serialize and Deserialize Binary Tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/?envType=study-plan&id=data-structure-ii)

## Solution

- Split logic into several small functions.
- `serialize(root: TreeNode | null): string`
  1. Using BFS algorithm, push all nodes into array in BFS order. `null` node should be kept in this case.
  2. Trim trailing `null`s in the array.
  3. Convert all nodes into number value or `null`.
  4. Join the array by `','`.
- `deserialize(data: string): TreeNode | null`
  1. Reverse engineer the BFS algorithm. Split `data` into value array.
  2. Pick first element of the `serialized` array and convert it into `TreeNode`.
  3. Every next two elements in `serialized` is `left`, `right` nodes of a queued node.
  4. Repeat until the `serialized` array to be empty.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function serialize(root: TreeNode | null): string {
  let serialized: (TreeNode | null)[] = [];

  const queue = [root];
  while (queue.length) {
    const node = queue.shift();
    serialized.push(node);
    if (node) {
      queue.push(node.left);
      queue.push(node.right);
    }
  }

  return filterTrailingNulls(serialized).map(toString).join(",");
}

function toString(node: TreeNode | null): string {
  return node?.val.toString() ?? "null";
}

function filterTrailingNulls(array: (TreeNode | null)[]): (TreeNode | null)[] {
  let index = array.length - 1;
  for (; index >= 0; index--) if (array[index] !== null) break;
  return array.slice(0, index + 1);
}

function deserialize(data: string): TreeNode | null {
  const serialized = data.split(",");

  const root = toNode(serialized.shift());
  const queue = [root];
  while (serialized.length) {
    const node = queue.shift();
    [node.left, node.right] = [serialized.shift(), serialized.shift()].map(
      toNode
    );
    if (node.left) queue.push(node.left);
    if (node.right) queue.push(node.right);
  }

  return root;
}

function toNode(val: string): TreeNode | null {
  if (!val || val === "null") return null;
  return new TreeNode(+val);
}
```

## Other's Solution

- If we use DFS algorithm with more memory space, code lines can be more concise.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function serialize(root: TreeNode | null): string {
  if (!root) return "null";
  return [root.val, serialize(root.left), serialize(root.right)].join(",");
}

function deserialize(data: string): TreeNode | null {
  function dfs(values: string[]): TreeNode | null {
    const value = values.shift();
    if (value === "null") return null;
    return new TreeNode(+value, dfs(values), dfs(values));
  }
  return dfs(data.split(","));
}
```
