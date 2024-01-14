# [[LeetCode] 443. String Compression](https://leetcode.com/problems/string-compression/description)

## Problem

> Given an array of characters chars, compress it using the following algorithm:
>
> Begin with an empty string s. For each group of consecutive repeating characters in chars:
>
> If the group's length is 1, append the character to s.
> Otherwise, append the character followed by the group's length.
> The compressed string s should not be returned separately, but instead, be stored in the input character array chars. Note that group lengths that are 10 or longer will be split into multiple characters in chars.
>
> After you are done modifying the input array, return the new length of the array.
>
> You must write an algorithm that uses only constant extra space.

## Solution

```typescript
function compress(chars: string[]): number {
  let s = "";

  for (let i = 0; i < chars.length; i++) {
    let group = chars[i];
    let count = 1;
    while (i < chars.length - 1 && group === chars[i + 1]) {
      count++;
      i++;
    }
    s += group;
    if (count > 1) s += count;
  }

  for (let i = 0; i < s.length; i++) chars[i] = s[i];
  return s.length;
}
```
