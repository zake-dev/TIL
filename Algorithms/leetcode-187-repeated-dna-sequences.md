# [LeetCode] 187. Repeated DNA Sequences

## Problem

> The **DNA sequence** is composed of a series of nucleotides abbreviated as `'A'`, `'C'`, `'G'`, and `'T'`.
>
> - For example, `"ACGAATTCCG"` is a **DNA sequence**.

> When studying **DNA**, it is useful to identify repeated sequences within the DNA.
> Given a string `s` that represents a **DNA sequence**, return all the **`10`-letter-long** sequences (substrings) that occur more than once in a DNA molecule. You may return the answer in **any order**.
> [[LeetCode] 187. Repeated DNA Sequences](https://leetcode.com/problems/repeated-dna-sequences/description/?envType=study-plan&id=data-structure-ii)

## Solution

- Register all **`10`-letter-long** sequences into `counter`, which is a hash table.
- Filter counter that its `count` is bigger than `1`.
- Take sequences only from the filtered counter.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function findRepeatedDnaSequences(s: string): string[] {
  const counter = new Map<string, number>();
  for (let i = 0; i <= s.length - 10; i++) {
    const sequence = s.slice(i, i + 10);
    const count = (counter.get(sequence) ?? 0) + 1;
    counter.set(sequence, count);
  }
  return [...counter.entries()]
    .filter(([_, count]) => count > 1)
    .map(([sequence]) => sequence);
}
```

## Other's Solution

- Also this problem can be solved with hash sets.
- Use `seen` and `repeated` hash sets to find repeated DNA sequences.
- Time Complexity: **O(n)**, Space Complexity: **O(n)**

```typescript
function findRepeatedDnaSequences(s: string): string[] {
  const [seen, repeated] = [new Set(), new Set()];
  for (let i = 0; i <= s.length - 10; i++) {
    const sequence = s.slice(i, i + 10);
    if (seen.has(sequence)) repeated.add(sequence);
    seen.add(sequence);
  }
  return Array.from(repeated);
}
```
