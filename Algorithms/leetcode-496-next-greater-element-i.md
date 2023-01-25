# [LeetCode] 496. Next Greater Element I

## Problem

> The **next greater element** of some element `x` in an array is the **first greater element** that is **to the right** of `x` in the same array.
> You are given two **distinct 0-indexed** integer arrays `nums1` and `nums2`, where `nums1` is a subset of `nums2`.
> For each `0 <= i < nums1.length`, find the index `j` such that `nums1[i] == nums2[j]` and determine the **next greater element** of `nums2[j]` in `nums2`. If there is no next greater element, then the answer for this query is `-1`.
> Return _an array `ans` of length `nums1`.length such that `ans[i]` is the **next greater element** as described above_.
> [[LeetCode] 496. Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/description/?envType=study-plan&id=programming-skills-i)

## Solution

- Create a hash map of next greater elements.
  - Iterate over `nums2`, push `node` into a stack.
  - Pick top node in the stack and compare with current `node`.
  - If current `node` is greater than popped one, store such pair into the hash map.
  - Keep take top node in the stack until current `node` gets smaller or be equal.
- Map `nums` with calculated hash map.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function nextGreaterElement(nums1: number[], nums2: number[]): number[] {
  const hashMap = toNextGreaterElementMap(nums2);
  return nums1.map((n) => hashMap.get(n) ?? -1);
}

function toNextGreaterElementMap(nums: number[]): Map<number, number> {
  const hashMap = new Map<number, number>();
  const stack: number[] = [];
  for (const num of nums) {
    if (!stack.length) {
      stack.push(num);
      continue;
    }

    while (stack.length) {
      const last = stack.pop();
      if (last < num) hashMap.set(last, num);
      else {
        stack.push(last);
        break;
      }
    }
    stack.push(num);
  }
  return hashMap;
}
```

## Other's Solution

- This is the most optimized version of solutions.
