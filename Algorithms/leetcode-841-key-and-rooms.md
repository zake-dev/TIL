# [LeetCode] 841. Key and Rooms

## Problem

> There are `n` rooms labeled from `0` to `n - 1` and all the rooms are locked except for room `0`. Your goal is to visit all the rooms. However, you cannot enter a locked room without having its key.
> When you visit a room, you may find a set of **distinct keys** in it. Each key has a number on it, denoting which room it unlocks, and you can take all of them with you to unlock the other rooms.
> Given an array `rooms` where `rooms[i]` is the set of keys that you can obtain if you visited room `i`, return _`true` if you can visit all the rooms, or `false` otherwise_.
> [[LeetCode] 841. Key and Rooms](https://leetcode.com/problems/keys-and-rooms/description/)

## Solution

- Using DFS algorithm, find that all rooms are reachable from room `0`.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function canVisitAllRooms(rooms: number[][]): boolean {
  function visitRooms(room: number, visited: boolean[]): boolean[] {
    if (visited[room]) return visited;
    visited[room] = true;
    rooms[room].forEach((room) => visitRooms(room, visited));
    return visited;
  }

  const visited = new Array(rooms.length).fill(false);
  return visitRooms(0, visited).every((v) => v);
}
```

## Other's Solution

- This is a simple DFS problem.
