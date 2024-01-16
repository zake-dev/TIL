# [[LeetCode] 238. Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/description)

# Solution - TypeScript

```typescript
function productExceptSelf(nums: number[]): number[] {
  const products = Array(nums.length).fill(1);
  for (let left = 1; left < nums.length; left++) {
    products[left] *= products[left - 1] * nums[left - 1];
  }

  let product = 1;
  for (let right = nums.length - 2; right >= 0; right--) {
    product *= nums[right + 1];
    products[right] *= product;
  }

  return products;
}
```
