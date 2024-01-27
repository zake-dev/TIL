# [[LeetCode] 71. Simplify Path](https://leetcode.com/problems/simplify-path/description)

# Solution - TypeScript

```typescript
function simplifyPath(path: string): string {
  const directories = path.split(/\/+/g);

  const simplified: string[] = [];
  for (const directory of directories) {
    if (directory === "." || directory === "") continue;
    if (directory === "..") {
      simplified.pop();
      continue;
    }
    simplified.push(directory);
  }

  return "/" + simplified.join("/");
}
```
