# [LeetCode] 208. Implement Trie (Prefix Tree)

## Problem

> A trie (pronounced as "try") or **prefix tree** is a tree data structure used to efficiently store and retrieve keys in a dataset of strings. There are various applications of this data structure, such as autocomplete and spellchecker.
> Implement the Trie class:
>
> - `Trie()` Initializes the trie object.
> - `void insert(String word)` Inserts the string `word` into the trie.
> - `boolean search(String word)` Returns `true` if the string `word` is in the trie (i.e., was inserted before), and false otherwise.
> - `boolean startsWith(String prefix)` Returns `true` if there is a previously inserted string `word` that has the prefix `prefix`, and `false` otherwise.

> [[LeetCode] 208. Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/description/)

## Solution

- Create a class `TrieNode` to store each characters of `word` as a `node`.
- `TrieNode` stores `children` which is a hash map of `(character, TrieNode)` pair.
- Also every `TrieNode` has a boolean flag named `end` which indicates there are words ended with this node in the `Trie`.
- `insert`, `search`, `prefix` will take **O(n)** time which is the length of the given `word`. However, it will take `26`(count of lowercase English letters) \* `m`(inserted words count) space at maximum.
- Time Complexity: `insert` **O(n)** `search` **O(n)** `prefix` **O(n)**, Space Complexity: **O(m \* n)**

```typescript
class TrieNode {
  children: Map<string, TrieNode>;
  end: boolean;

  constructor() {
    this.children = new Map<string, TrieNode>();
    this.end = false;
  }
}

class Trie {
  #root: TrieNode;

  constructor() {
    this.#root = new TrieNode();
  }

  insert(word: string): void {
    let current = this.#root;
    for (const character of word) {
      if (!current.children.has(character))
        current.children.set(character, new TrieNode());
      current = current.children.get(character);
    }
    current.end = true;
  }

  search(word: string): boolean {
    let current = this.#root;
    for (const character of word) {
      if (!current.children.has(character)) return false;
      current = current.children.get(character);
    }
    return current.end;
  }

  startsWith(prefix: string): boolean {
    let current = this.#root;
    for (const character of prefix) {
      if (!current.children.has(character)) return false;
      current = current.children.get(character);
    }
    return true;
  }
}
```

## Other's Solution

- This is a simple implementation problem. Similar solutions exist.
