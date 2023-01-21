# [LeetCode] 1491. Average Salary Excluding the Minimum and Maximum Salary

## Problem

> You are given an array of **unique** integers `salary` where `salary[i]` is the salary of the ith employee.
> Return _the average salary of employees excluding the minimum and maximum salary. Answers within `10^-5` of the actual answer will be accepted_.
> [[LeetCode] 1491. Average Salary Excluding the Minimum and Maximum Salary](https://leetcode.com/problems/average-salary-excluding-the-minimum-and-maximum-salary/?envType=study-plan&id=programming-skills-i)

## Solution

- There two ways to solve this problem. One is a bit slower but has good readability, and another is fast but it gives up regarding to readability.
- This version of answer cares about readability not the speed.
- Time Complexity: **O(n)**, Space Complexity: **O(1)**

```typescript
function average(salary: number[]): number {
  const min = Math.min(...salary);
  const max = Math.max(...salary);
  const sum = salary.reduce((a, b) => a + b);
  return (sum - min - max) / (salary.length - 2);
}
```

## Other's Solution

- Other optimized version is below.

```typescript
function average(salaries: number[]): number {
  let min = Infinity;
  let max = -Infinity;
  let sum = 0;
  for (const salary of salaries) {
    min = salary < min ? salary : min;
    max = salary > max ? salary : max;
    sum += salary;
  }
  return (sum - min - max) / (salaries.length - 2);
}
```
