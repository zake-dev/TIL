# [[LeetCode] 68. Text Justification](https://leetcode.com/problems/text-justification/description)

# Solution - TypeScript

```typescript
function buildNormalLine(words: string[], maxWidth: number): string {
  const lineLength = words.reduce((a, b) => a + b.length, 0);
  const totalSpaces = maxWidth - lineLength;
  const baseSpace = Math.floor(totalSpaces / (words.length - 1));
  let remainingSpace = totalSpaces % (words.length - 1);
  for (let i = 0; i < words.length - 1; i++) {
    if (remainingSpace > 0) {
      words[i] += " ";
      remainingSpace--;
    }
    words[i] += " ".repeat(baseSpace);
  }

  return words.join("").padEnd(maxWidth);
}

function buildLastLine(words: string[], maxWidth: number): string {
  return words.join(" ").padEnd(maxWidth);
}

function fullJustify(words: string[], maxWidth: number): string[] {
  const lines = [] as string[][];

  let currentLength = 0;
  let line = [] as string[];
  for (const word of words) {
    if (currentLength + word.length + line.length > maxWidth) {
      lines.push(line);
      currentLength = 0;
      line = [];
    }
    line.push(word);
    currentLength += word.length;
  }
  if (line.length > 0) lines.push(line);

  return lines.map((line, index) =>
    index !== lines.length - 1
      ? buildNormalLine(line, maxWidth)
      : buildLastLine(line, maxWidth)
  );
}
```
