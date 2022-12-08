# How to Make Lazy Evaluated Function with Generator Syntax

JavaScript has a weird syntax named **generator**. Compared to a normal function, generator function allows you to create infinite iterator, lazy evaluated function, etc. Here is how to implement those in JavaScript.

## Generator Syntax

To declare a **generator function**, put a single _asterisk_ after `function`, like `function* name() {...}`. After then, you can `yield` some value inside of the generator to return.

There are some rules to use **generaotr function**:

1. You cannot declare with _arrow function_.
2. Calling a generator function will always return a **_iterator_**.
3. To retrieve value from it, simply call `iterator.next()`.
4. When the `iterator` reaches its end, you will get `undefined` value with `done` flag, like `{ value: undefined, done: true }`.
5. _returned value_ from the generator with `return` statement will be served at last iteration with `done` flag, like `{ value: returned value, done: true }`
6. Also you can access values of iterator by using _spread operator_ `[...iterator]`, or `for...of` loop.

```javascript
function* colorGenerator() {
  console.log("Color Generator Start.");
  yield "red";
  yield "blue";
  yield "green";
}

const colors = colorGenerator();
for (const color of colors) {
  console.log(color);
}
```

What will be the result of above code? When the generator is created, nothing go to happen because calling generator function returns an iterator without iteration. `console.log` on the first line will be executed when the first iterator value has been accessed which is `red`.

## Infinite Iterator

```javascript
function* generateNaturalNumbers() {
  for (let i = 1; true; i++) yield i;
}
```

**Generator function** does not always have the end. It can be endless iterator like above. Above generator returns `1` to `Infinity` whenever the next value is requested. As this generator returns infinite iterator, you cannot convert it into array with _spread operator_.

## Lazy Evaluated Function

You can make a lazy evaluated function with generators too. Let's think about the function add up `2` to all the given numbers, then multiply those with `10`, power by `3`, subtract by `8` and return _first three numbers_ only.

The function can be written like:

```javascript
function calculateAndTakeThreeNumbers(numbers) {
  return numbers
    .map((n) => n + 2)
    .map((n) => n * 10)
    .map((n) => n * n)
    .map((n) => n - 8)
    .slice(0, 3);
}
```

However, above function can be slow when the length of `numbers` getting bigger, even the function only needs _first three numbers_ as a result.

Generator function is able to solve these kind of problems as generator does not evaluate the value until its iterator being called. To achieve this, let's make some util functions that work with generators.

```javascript
const map = (f) =>
  function* (iterable) {
    for (const x of iterable) yield f(x);
  };

const take = (n) =>
  function* (iterable) {
    let i = 0;
    for (const x of iterable) {
      if (i >= n) return;
      yield x;
      i++;
    }
  };
```

Now you can `map` any iterables without _just-in-time-evaluation_. The function passed to the `map` function will wait for the evaluation until the next value of iterator being called.

Likewise, `take` function will wait for the calling, and will return values only the given times. Be careful that you have to use `for...of` loop to access `iterator` and other `iterables` at once.

```javascript
const pipe = (x0, ...fns) => fns.reduce((x, f) => f(x), x0);

function calculateAndTakeThreeNumbers(numbers) {
  return [
    ...pipe(
      numbers,
      map((n) => n + 2),
      map((n) => n * 10),
      map((n) => n * n),
      map((n) => n - 8),
      take(3)
    ),
  ];
}
```

Isn't it fantastic? Now the evaluation will only be executed on `spread operator`, which means this function will not be slowed by the length of the `numbers`.

<sub>**REFERENCES**</sub>
<sub>[1. Why Would Anyone Need JavaScript Generator Functions / James Sinclair](https://jrsinclair.com/articles/2022/why-would-anyone-need-javascript-generator-functions/)</sub>
