# [LeetCode] 290. Word Pattern

## Problem

> Given a `pattern` and a string `s`, find if `s` follows the same pattern.
> Here **follow** means a full match, such that there is a bijection between a letter in pattern and a **non-empty** word in `s`.
> [[LeetCode] 290. Word Pattern](https://leetcode.com/problems/word-pattern/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Iterate over the given `pattern` and `words`, record a `key`, `value` in hash map.
- Double check with hash set that `key - value` pair is identical.
- Handle edge case: the length of `pattern` should be equal to `words`.
- Runtime Complexity: **O(n)**

```typescript
function wordPattern(pattern: string, s: string): boolean {
  const words = s.split(" ");
  if (pattern.length !== words.length) return false;

  const patternMap = new Map<string, string>();
  const checkedWords = new Set();
  for (let i = 0; i < words.length; i++) {
    const key = pattern[i];
    const value = words[i];
    if (!patternMap.has(key)) {
      if (checkedWords.has(value)) return false;
      patternMap.set(key, value);
      checkedWords.add(value);
      continue;
    }
    if (patternMap.get(key) !== value) return false;
  }
  return true;
}
```

## Other's Solution

- No other intuitive solution exists.
