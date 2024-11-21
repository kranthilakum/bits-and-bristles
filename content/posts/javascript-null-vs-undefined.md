---
title: JavaScript null vs undefined
date: 2018-08-13T09:55:46+05:30
draft: false
categories:
- "javascript"
tags:
- "javascript"
- "primitive"
- "types"
- "datatypes"
- "null"
- "undefined"
- "object"
---

`null` and `undefined` are special _values or types_ in Javacript. 

Conceptually, `undefined` indicates the absence of a value, while `null` indicates the absence of an object value.

------

### `null`

Null is a nullable type of JavaScript. It allows a variable to set to a value `null`. Null is precisely defined as no value. It is a special value that represents the absence of any object value.

```js
foo; // ReferenceError: foo is not defined

var foo = null;

typeof foo; // "object"
```

`null` is a primitive value. It is not possible to assign a property to `null` because it is _not an object_.

`null` is a value that explicitly represents the intentional absence of any object value. It indicates that a variable points to _no object_ or that a property of an object does not have a value.

```js
let obj; // undefined

// explicitly set obj to null
obj = null; // null -> intentional absence of any object value

typeof obj; // 'object'
```

`obj` was declared but not assigned a value, so it is `undefined`. When `obj` is assigned `null`, it indicates that `obj` points to _no object_, but now the `obj` variable exists and has a value, which is `null`.

`null` is where the variable or property exists, but it does not have a value. It is a way to indicate that the variable or property is intentionally empty.

```js
obj = { name: 'obj' }

obj.name // 'obj'

// accessing a property that does not exist
obj.size // undefined

// setting the property to null to indicate absence of value
obj.size = null

obj.size // null

typeof obj.size; // 'object'
```

`null`, can be tested by the `typeof` operator. `typeof null` returns `"object"`, so one has to use `=== null` to test for null.

All primitive types have have their corresponding object wrapper type except for `null` and `undefined`.

`undefined` is a value that represents the unintentional absence of any value. It is the _default value of a variable_ that has been declared but not assigned a value. It is also the value of a property that has not been assigned a value or the value returned by a function that does not explicitly return a value.

```js
var x;
// x is declared but not assigned a value
console.log(x); // undefined

var obj = {};
// obj.prop is not assigned a value
console.log(obj.prop); // undefined

function foo() {}
// foo does not return a value
console.log(foo()); // undefined
```

```js
// function that checks if a parameter has a value
function myFunction(param) {
  if (param === null) { // check for null with strict equality `===`
    console.log('The parameter has no value');
  } else {
    console.log(`The parameter has a value: ${param}`);
  }
}

myFunction(null); // The parameter has no value
myFunction('Hello World'); // The parameter has a value: Hello World
```

----

### `undefined` is a global variable

```js
foo; // ReferenceError: foo is not defined

typeof foo; // "undefined"
```

`foo` is undefined because there is no notion of it in the current scope. It is not defined in the current scope, so it is `undefined`. When you try to reference a variable that has not been declared, you get a `ReferenceError`.

`undefined` is an identifier for a _property of the global object_, i.e., it is a global variable. It is can be accessed as `window.undefined` in the browser or `global.undefined` in Node.js.

It is possible to create a local variable with the name `undefined` that shadows the global `undefined` variable. This can lead to unexpected behavior and should be avoided.

```js
function test() {
  let undefined = 5;
  console.log(undefined); // 5
  console.log(typeof undefined); // "number"
}

test();
```

`null` is a reserved keyword unlike `undefined`.

----

`null` and `undefined` are both falsy values, i.e., they evaluate to `false` in a boolean context.

> Beware of equality comparisons between `null` and `undefined`. They are not equal to each other, but they are both falsy values.

```js
typeof null // "object"

typeof undefined // "undefined"

// loose equality performs type coercion on operands and compares values
null == undefined // true

null !== undefined // true

null === undefined // false

null == null // true

undefined == undefined // true
```

`null` is not, conceptually, the same as `false` or `""`.

```js
!null // true

null == false // false

null === false // false

null == "" // false

null === "" // false
```

```js
!undefined // true

undefined == false // false

undefined === false // false

undefined == "" // false

undefined === "" // false
```

----

### `null` is not an object, but a bug!

```js
typeof null // "object"
```

The reason that typeof check returns `"object"` for `null` is a bug in the original implementation of JavaScript. It is a mistake that has been kept in the language for backward compatibility reasons. It was probably inspired by Lisp, where a similar construct `nil` was used to represent the absence of a value or empty list which was represented by object.

----

### Links

- [null](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/null), MDN.
- [Why is null an object and what's the difference between null and undefined?](https://stackoverflow.com/q/801032)
- [Null object pattern](https://en.wikipedia.org/wiki/Null_object_pattern)
- [Crockford on JavaScript - Volume 1: The Early Years](https://www.youtube.com/watch?v=JxAXlJEmNMg&ab_channel=YUILibrary)
- [An explanation of nil](https://www.gnu.org/software/emacs/manual/html_node/eintr/nil-explained.html), Lisp.
- [Homoiconicity](https://en.wikipedia.org/wiki/Homoiconicity)
- [Why does loose equals on null and undefined returns true?](https://stackoverflow.com/q/38630411)
