# [[LeetCode] 345. Reverse Vowels of a String](https://leetcode.com/problems/reverse-vowels-of-a-string/description)

## Problem

> Given a string `s`, reverse only all the vowels in the string and return it.
>
> The vowels are `'a'`, `'e'`, `'i'`, `'o'`, and `'u'`, and they can appear in both lower and upper cases, more than once.

## Solution

- Find indices of vowels first.
- Split given `s` into `characters` array and, swap vowels.
- Return joined `characters`.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function reverseVowels(s: string): string {
  const vowelIndices = [];
  for (let i = 0; i < s.length; i++) {
    if (isVowel(s[i])) vowelIndices.push(i);
  }

  const characters = s.split("");
  for (let i = 0; i < vowelIndices.length / 2; i++) {
    swap(
      characters,
      vowelIndices[i],
      vowelIndices[vowelIndices.length - 1 - i]
    );
  }

  return characters.join("");
}

function isVowel(ch: string): boolean {
  return ["a", "e", "i", "o", "u", "A", "E", "I", "O", "U"].includes(ch);
}

function swap(arr: any[], i: number, j: number): void {
  const temp = arr[i];
  arr[i] = arr[j];
  arr[j] = temp;
}
```
