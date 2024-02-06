# [[LeetCode] 117. Populating Next Right Pointers in Each Node II](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/description)

# Solution - TypeScript

```typescript
function connect(root: Node | null): Node | null {
  function hasNoChildren(node: Node | null) {
    return node?.left === null && node?.right === null;
  }

  function recursive(node: Node | null): void {
    let nextParent = node.next;
    while (hasNoChildren(nextParent)) nextParent = nextParent.next;

    let next = nextParent?.left ?? nextParent?.right ?? null;
    if (node.right !== null) node.right.next = next;
    if (node.left !== null) node.left.next = node?.right ?? next;

    if (node.right !== null) recursive(node.right);
    if (node.left !== null) recursive(node.left);
  }

  if (root === null) return root;
  recursive(root);
  return root;
}
```
