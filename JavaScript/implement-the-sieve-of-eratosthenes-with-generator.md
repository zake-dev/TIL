# Implement the Sieve of Eratosthenes with Generator

First of all, this is not an optimized solution to calculate prime numbers, but it shows how to use **generator function** to implement lazy evaluated _the Sieve of Eratosthenes_.

```javascript
function* naturalNumbers() {
  for (let i = 1; true; i++) yield i;
}
```

You need a infinite number generator first. These numbers will be filtered by `sieve` function later.

```javascript
function* filter(p, iterable) {
  for (const x of iterable) if (p(x)) yield x;
}

function pop(iterator) {
  const result = iterator.next();
  if (result.done) return;
  return [result.value, iterator];
}

function* drop(n, iterable) {
  let i = 0;
  for (const x of iterable) {
    if (i >= n) yield x;
    i++;
  }
}

function take(n) {
  return function* (iterable) {
    let i = 0;
    for (const x of iterable) {
      if (i >= n) return;
      yield x;
      i++;
    }
  };
}
```

These four util functions will help to build the sieve. `filter` functions is a generator way of `Array.prototype.filter`.  
`pop` function slices first value from the given iterator and return such `value` and `rest` iterator.  
`drop` function will cut off first `n` elements of the given `iterable`.  
The last function `take` will drop all the rest elements except first `n` elements of the given `iterable`.

```javascript
function* sieve(numbers) {
  const result = pop(numbers);
  if (!result) return;
  const [n, rest] = result;
  yield n;
  yield* sieve(filter((x) => x % n !== 0, rest));
}
```

The core logic of _the Sieve of Eratosthenes_ is picking up and filtering. First, pick up the number from the sieve, named `n`. Next, filter all multiples of `n` in natural numbers. These simple progress will filter _non-prime numbers_ from the given `numbers`.

Here is a special keyword `yield*`. This keyword pass the evaluation to delegated generator function specified after the keyword. In this case, next `sieve` call nested `sieve` generator function with filtered and popped iterator instead of original.

```javascript
const primes = () => sieve(drop(1, naturalNumbers()));
console.log([...take(10)(primes())]);
```

You can take a result like above.

<sub>**REFERENCES**</sub>
<sub>[1. Why Would Anyone Need JavaScript Generator Functions / James Sinclair](https://jrsinclair.com/articles/2022/why-would-anyone-need-javascript-generator-functions/)</sub>
