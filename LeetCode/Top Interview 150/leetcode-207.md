# [[LeetCode] 207. Course Schedule](https://leetcode.com/problems/course-schedule/description)

# Solution - TypeScript

```typescript
function canFinish(numCourses: number, prerequisites: number[][]): boolean {
  const graph = new Map<number, number[]>();
  for (const [course, prerequisite] of prerequisites) {
    if (!graph.has(prerequisite)) graph.set(prerequisite, []);
    graph.get(prerequisite).push(course);
  }

  function hasCycle(
    node: number,
    visited: boolean[],
    stack: boolean[]
  ): boolean {
    if (stack[node]) return true;
    if (visited[node]) return false;
    visited[node] = true;
    stack[node] = true;
    for (const neighbor of graph.get(node) ?? []) {
      if (hasCycle(neighbor, visited, stack)) return true;
    }

    stack[node] = false;
    return false;
  }

  const visited = Array(numCourses).fill(false);
  const stack = Array(numCourses).fill(false);
  for (let i = 0; i < numCourses; i++) {
    if (!graph.has(i)) continue;
    if (hasCycle(i, visited, stack)) return false;
  }
  return true;
}
```
