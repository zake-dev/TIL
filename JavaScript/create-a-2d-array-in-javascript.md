# Create an Empty 2D Array in JavaScript

You have to be aware when you create an empty 2D array in Javascript.
If you use `Array.prototype.fill` function with `object` type value, it will mess up your logic in some case.  
Look at the code below.

```javascript
const matrix1 = new Array(3).fill(new Array(3));
const matrix2 = Array.from({ length: 3 }, (_) => new Array(3));
```

It looks same the way to create `matrix1` and `matrix2` is, and the way to create `matrix2` seems little bit verbose.  
However, there is a huge difference between both.  
If you try to put some elements in `matrix1`, you will recognize you've made a mistake.

```javascript
let num = 1;
for (let i = 0; i < 3; i++) for (let j = 0; j < 3; j++) matrix1[i][j] = num++;
console.log(matrix1);
```

You will expect that the above code lines will print like `[[1, 2, 3], [4, 5, 6], [7, 8, 9]]` but you will meet the result like `[[7, 8, 9], [7, 8, 9], [7, 8, 9]]`.  
Why this happened?  
When `Array.prototype.fill` function is called on the first line, complier will create an empty array having length of 3 first. After then, `matrix1` is filled by the reference of the created empty array. It makes all the child arrays in `matrix1` indicates same array in memory!

That's why you should prefer `matrix2` way over `matrix1` way despite its syntax looks ugly.  
The callback function passed by argument will create new array every time rather than create once and pass a reference.
