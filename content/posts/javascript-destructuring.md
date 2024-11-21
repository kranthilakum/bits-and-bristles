---
id: javascript-destructuring
title: JavaScript Destructuring
date: 2018-08-14T08:55:46+05:30
draft: false
categories:
  - "javascript"
tags:
  - "javascript"
  - "destructuring"
  - "es6"
  - "es2015"
---

Destructuring is a feature in JavaScript that allows you to extract values from arrays or objects and assign them to variables in a more concise and readable way.

## Destructuring assignment

- Destructuring is a feature in JavaScript that allows you to unpack elements from arrays or objects and assign them to variables.
- Destructuring can be a powerful tool for extracting and assigning values in a concise and readable way.
- The initial array or object shall remain unmodified during the destructuring process, so no mutation occurs.
- When using destructuring assignment, make sure to provide variable names to empty slots to avoid data loss.

### Array destructuring `[a, b] = arr`

#### Use case 1: Extract values from an array

```js
let [firstName, lastName] = ["Jack", "Sparrow"];
firstName; // "Jack"
lastName; // "Sparrow"
```

Extract values from a given array and assign them to variables

#### Use case 2: Ignore elements in an array

```js
let [, firstName, lastName] = ["Captain", "Jack", "Sparrow"];
firstName; // "Jack"
lastName; // "Sparrow"
```

Ignore elements in the array by using a comma without a variable name in the destructuring pattern and assign the rest of the elements to respective variables

#### Use case 3: Assign default values

```js
let [firstName, lastName, suffix = "Jr."] = ["Jack", "Sparrow"];
suffix; // "Jr."
```

Assign default values to variables in case the value is `undefined` or `null`

#### Use case 4: Swap variables

```js
let a = 1;
let b = ((2)[(a, b)] = [b, a]);
a; // 2
b; // 1
```

Swap the values of two variables without using a temporary variable.

#### Use case 5: Rest element

```js
let [first, ...rest] = [1, 2, 3, 4, 5];
first; // 1
rest; // [2, 3, 4, 5]

let [a, b, ...rest] = [1, 2, 3, 4, 5];
a; // 1
b; // 2
rest; // [3, 4, 5]
```

Use the rest operator (...) to accumulate and assign the remaining elements of an array to a single variable. The remaining elements are not destructured and are assigned as an array.

#### Use case 6: Nested destructuring

```js
let [a, [b, c]] = [1, [2, 3]];
a; // 1
b; // 2
c; // 3
```

Destructure nested arrays by using nested destructuring patterns.

#### Use case 7: Ignore the rest of the elements

```js
let [a, b] = [1, 2, 3, 4, 5];
a; // 1
b; // 2
```

Ignore the rest of the elements in an array by using a destructuring pattern with fewer variables than the number of elements in the array.

#### Use case 8: Returning multiple values from a function

```js
function getPerson() {
  return ["Jack", "Sparrow"];
}

let [firstName, lastName] = getPerson();
firstName; // "Jack"
lastName; // "Sparrow"
```

#### Use case 9: When array has empty slots

```js
let [firstName, middleName, lastName] = ["Jack", , "Sparrow"];
firstName; // "Jack"
middleName; // undefined
lastName; // "Sparrow"
```

```js
let [firstName, , lastName] = ["Jack", undefined, "Sparrow"];
firstName; // "Jack"
lastName; // "Sparrow"
```

---

#### More examples

```js
var arr = [1, , ,];
var [a = 3, b = 6, c = 9, d = 12] = arr;
console.log(a, b, c, d); // 1 6 9 12
```

```js
var arr = [1];
var [a, b] = arr;
console.log(a, b); // 1 undefined
```

If there are more variables than the length of the array, the value of the variable will be `undefined`.

```js
var [a, ...b, c] = [1, 2, 3, 4, 5]
console.log(a, b, c) // SyntaxError: rest element may not have a trailing comma
```

The rest element must be the last element in the destructuring pattern.

Spread a string into an array of characters and destructure it

```js
var [a, b, c] = [..."abc"];

console.log(a, b, c); // a b c
```

Add new elements to the array with spread syntax and destructure them

```js
var [a, b, c, ...d] = [1, 2, ...[3, 4, 5]];

console.log(a, b, c, d); // 1 2 3 [4, 5]
```

---

### Object destructuring `{ a, b } = obj`

#### Use case 1: Extract values from an object

```js
let { firstName, lastName } = { firstName: "Jack", lastName: "Sparrow" };
firstName; // "Jack"
lastName; // "Sparrow"

let person = { firstName: "Jack", lastName: "Sparrow" };
let { firstName, lastName } = person;
firstName; // "Jack"
lastName; // "Sparrow"
```

Extract values from a given object and assign them to variables with the same name as the object keys

#### Use case 2: Assign default values

```js
let {
  firstName,
  lastName,
  suffix = "Jr.",
} = { firstName: "Jack", lastName: "Sparrow" };
suffix; // "Jr."
```

Assign default values to variables in case the value is `undefined` or `null`

#### Use case 3: Assign to different variable names

```js
let { firstName: first, lastName: last } = {
  firstName: "Jack",
  lastName: "Sparrow",
};
first; // "Jack"
last; // "Sparrow"
```

Assign values to variables with different names than the object keys

#### Use case 4: Nested destructuring

```js
let {
  a,
  b: { c, d },
} = { a: 1, b: { c: 2, d: 3 } };
a; // 1
c; // 2
d; // 3
```

Destructure nested objects by using nested destructuring patterns.

#### Use case 5: Rest element

```js
let { a, ...rest } = { a: 1, b: 2, c: 3 };
a; // 1
rest; // { b: 2, c: 3 }
```

Use the rest operator (...) to accumulate and assign the remaining properties of an object to a single variable. The remaining properties are not destructured and are assigned as an object.

---

#### More examples

```js
var { name, age, occupation } = { name: "Jack", occupation: "Pirate" };
console.log(name, age, occupation); // Jack undefined Pirate
```

If the object does not have a property that is being destructured, the value of the variable will be `undefined`.

```js
var name, age;
var person = {name: "Jack", occupation: "Pirate"}
({name, age}) = person
console.log(name, age) // Jack undefined
```

Assign values to variables outside of the destructuring pattern by wrapping the pattern in parentheses.

```js
var obj = { a: 1, b: 2, c: 3 };
var { a, b, c } = obj;
console.log(a, b, c); // 1 2 3
```

```js
var obj = { a: 1, b: 2, c: 3 };
var { a, b, c, d } = obj;
console.log(a, b, c, d); // 1 2 3 undefined
```

If the object does not have a property that is being destructured, the value of the variable will be `undefined`.

```js
var obj = { a: 1, b: 2, c: 3 }
var { a, ...b, c } = obj
console.log(a, b, c) // SyntaxError: rest element may not have a trailing comma
```

The rest element must be the last element in the destructuring pattern.

---

### Links

- []()
- []()
