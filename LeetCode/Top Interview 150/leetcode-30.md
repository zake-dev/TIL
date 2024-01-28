# [[LeetCode] 30. Substring with Concatenation of All Words](https://leetcode.com/problems/substring-with-concatenation-of-all-words/description)

# Solution - TypeScript

```typescript
function toCounter(array: string[]): Map<string, number> {
  const map = new Map<string, number>();
  for (const element of array) map.set(element, (map.get(element) ?? 0) + 1);
  return map;
}

function findSubstring(s: string, words: string[]): number[] {
  const indices: number[] = [];
  const wordLength = words[0].length;
  const validCounter = toCounter(words);

  for (let i = 0; i < wordLength; i++) {
    let left = i;
    let right = i;
    let count = 0;
    const counter = new Map<string, number>();

    while (right + wordLength <= s.length) {
      const word = s.substring(right, right + wordLength);
      right += wordLength;

      if (validCounter.has(word)) {
        counter.set(word, (counter.get(word) ?? 0) + 1);
        count++;

        while (counter.get(word) > validCounter.get(word)) {
          const leftWord = s.substring(left, left + wordLength);
          counter.set(leftWord, counter.get(leftWord) - 1);
          count--;
          left += wordLength;
        }

        if (count === words.length) {
          indices.push(left);
        }
      } else {
        counter.clear();
        count = 0;
        left = right;
      }
    }
  }

  return indices;
}
```
