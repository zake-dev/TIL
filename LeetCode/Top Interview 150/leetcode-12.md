# [[LeetCode] 12. Integer to Roman](https://leetcode.com/problems/integer-to-roman/description)

# Solution - TypeScript

```typescript
function toPartialRoman(
  num: number,
  limit: number,
  large: string,
  medium: string,
  small: string
): string {
  const digit = Math.floor(num / limit);
  if (digit === 9) return small + large;
  else if (digit >= 5) return medium + small.repeat(digit - 5);
  else if (digit === 4) return small + medium;
  else return small.repeat(digit);
}

function intToRoman(num: number): string {
  let roman = "";
  const stream = [
    [1000, "", "", "M"],
    [100, "M", "D", "C"],
    [10, "C", "L", "X"],
    [1, "X", "V", "I"],
  ];
  for (const [limit, large, medium, small] of stream) {
    roman += toPartialRoman(
      num,
      limit as number,
      large as string,
      medium as string,
      small as string
    );
    num %= limit as number;
  }
  return roman;
}
```
