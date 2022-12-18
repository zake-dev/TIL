# [LeetCode] 238. Product of Array Except Self

## Problem

> Given an integer array `nums`, return _an array `answer` such that `answer[i]` is equal to the product of all the elements of `nums` except `nums[i]`_.
> The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.
> You must write an algorithm that runs in `O(n)` time and without using the division operation.
> [[LeetCode] 238. Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/description/?envType=study-plan&id=data-structure-ii)

## Solution

- I was not able to solve the problem within `O(n)` time. This solution is based on others'.
- Iterate over `nums` twice, increasing way and reversed way. Calculate _left product_ and _right product_ which are excluding `num` itself.
- Product `left` and `right`.
- Below code combines above logic to reduce runtime.
- Runtime Complexity: **O(n)**

```typescript
function productExceptSelf(nums: number[]): number[] {
  const n = nums.length;
  const result = new Array(n).fill(1);
  for (let i = 1; i < n; i++) result[i] = result[i - 1] * nums[i - 1];

  let right = 1;
  for (let i = n - 1; i >= 0; i--) {
    result[i] *= right;
    right *= nums[i];
  }

  return result;
}
```

## Other's Solution

- Most of solutions has minor differences with above solution.
