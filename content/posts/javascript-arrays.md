
---
title: JavaScript Arrays
date: 2018-08-17T09:55:46+05:30
draft: false
categories:
- "javascript"
tags:
- "javascript"
- "arrays"
---

### Initialize Arrays

```js
const arr1 = Array(5);
arr1.map(() => 0); // 5 empty slots
arr1.map((_, i) => i); // 5 empty slots

const arr2 = Array.from({ length: 2 }); // [undefined, undefined]

const arr2 = [...Array(2)]; // [undefined, undefined]
```

[What are empty slots?](https://stackoverflow.com/q/42519972)

```js
const arr1 = Array.from({ length: 2 });

arr1.map(() => 1) // [1, 1]

arr1.map((_, i) => i) // [0, 1]

arr1.map((_, i, a) => i / a.length) // [0, 0.5]
```

```js
const arr1 = Array.from({ length: 2 }, () => 0);
// [0, 0, 0, 0, 0]

// static array
const arr1 = Array.from({ length: 2 }, () => 1);
// [1, 1, 1, 1, 1]

// indexed array
const arr1 = Array.from({ length: 2 }, (_, i) => i);
// [0, 1, 2, 3, 4]
```

```js
const arr = Array(2)
// [empty x 2]

const arr0 = Array(2).fill();
// [undefined, undefined]

const arr1 = Array(5).fill(0);
// [0, 0, 0, 0, 0]

const arr2 = Array(5).fill().map(() => 0);
// [0, 0, 0, 0, 0]

const arr3 = Array(5).fill().map((_, i) => i);
// [0, 1, 2, 3, 4]
```

```js
const arr = new Array(3).fill(null); // [null, null, null]

const arr = new Array(3).fill(0); // [0, 0, 0]

const arr = new Array(3).fill(1); // [1, 1, 1]

const arr = new Array(3).fill(null).map((_, i) => i); // [0, 1, 2]
```

```js
const arr = Array(2); // [empty x 2]

arr.forEach(el => console.log(el)); // undefined, undefined
```

`Array.prototype.forEach` does not visit indices which have been deleted or elided; this is a process called __[Ellision]__(https://stackoverflow.com/q/27433075). So, it executes, but skips over every element. This is why `undefined` is logged twice.

__Illustration__:

```js
const log = (el, i) => console.log(`Index: ${i}, Element: ${el}`);

[1, 2, , , 5].forEach(log);
// Index: 0, Element: 1
// Index: 1, Element: 2
// Index: 4, Element: 5
```

Note that the deleted or elided values are not visited or logged. However, it is possible to visit if they were explicitly set to `undefined`.

---

The `Array(2)` creates an array with two "empty" places, since empty places are not iterable, we use `Array.apply` to bind a `this` object, which we set to `null`, and supply arguments as an _array_. It creates an array of `undefined` which is iterable and we can fill it with `map` or `forEach`.

```js
const arr = Array.apply(null, Array(2)) // [undefined, undefined]

arr.forEach(log);
// Index: 0, Element: undefined
// Index: 1, Element: undefined

arr.forEach((_, i) => arr[i] = 0); // [0, 0]

arr.forEach((_, i) => arr[i] = i); // [0, 1]
```

```js
Array.apply(null, Array(2)).map((_, i) => 0); // [0, 0]

Array.apply(null, Array(2)).map((_, i) => i); // [0, 1]
```

------

Initialize an array with a specific length and value using the Array constructor and `fill` method.

```js
const initializeArray = (length, value) => Array(length).fill(value);

initializeArray(5, 0); // [0, 0, 0, 0, 0]
```

Initialize an array with a specific length and map function.

```js
const initializeArray = (length, fn = (_, i) => i) => Array(length).fill(null).map(fn);

initializeArray(5); // [0, 1, 2, 3, 4]

initializeArray(5, (_, i) => i * 2); // [0, 2, 4, 6, 8]
```

[Source](https://www.30secondsofcode.org/js/s/array-initialization/)

------

### Remove empty slots from Array

```js
const arr = [1, 2, , , 5];

arr.filter(() => true); // [1, 2, 5]

arr.filter((x) => x); // [1, 2, 5]

arr.filter((x) => x !== undefined); // [1, 2, 5]
```

Use `Array.prototype.flat` to remove empty slots from an array. It creates a new array with all sub-array elements concatenated into it recursively up to the specified depth. If you do not specify a depth, it defaults to 1. If you have nested arrays, you can specify a depth to flatten them. You can also use `Infinity` to flatten all nested arrays. It removes empty slots from the array.

```js
const arr = [1, 2, , , 5];

arr.flat(); // [1, 2, 5]
```

```js
const arr = [1, [1, 2, , , [1, 2, , 4, 5]], 2, , 5];

arr.flat(2); // [1, 1, 2, 1, 2, 4, 5, 2, 5]
```

[Source](https://www.encodedna.com/javascript/how-to-remove-empty-slots-in-javascript-arrays.htm)

-------

Use a Proxy with a custom `has` trap to control which elements are visible to array iteration methods like `forEach`, `map`, `filter`, etc. The `has` trap gets called during iteration to check if an element exists in the array at a given index.

```js
const createArray = () => {
    const target = [];
    return new Proxy(target, {
        has: (target, prop) => !isNaN(prop) && prop < 5
    });
};

const arr = createArray();

arr[0] = 1;
arr[1] = 2;
arr[2] = undefined;
arr[3] = 4;
arr[4] = undefined;
arr[5] = 6;

arr.forEach(el => console.log(el)); // 1, 2, 4
```

------

