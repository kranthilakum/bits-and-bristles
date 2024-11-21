---
title: JavaScript Primitive Types
date: 2018-08-12T09:55:46+05:30
draft: false
categories:
- "javascript"
tags:
- "javascript"
- "primitive"
- "types"
- "datatypes"
---

There are 8 Data types in JavaScript.
1. Number
2. BigInt
3. String
4. Boolean
5. undefined
6. null
7. Symbol
8. Object

Except Object, the rest of the seven data types are called as Primitive data types.  These are the standard data types built into the language (aka. __built-in types__).

A Primitive data contains data that is not an Object.

A Primitive _doesn't have properties or methods_ but when you try to access a valid property on a Primitive, JavaScript auto-boxes the value into an ephemeral wrapper object and accesses the property on that Object instead. This wrapping is temporary and any changes made to this ephemeral object do not persist.

E.g. `"foo"` is a string which itself has no properties or methods, but `"foo".includes("f")` creates a String wrapper object and calls `String.prototype.includes()` on that object. 

All Primitives are __immutable__, meaning that once they are created, they cannot be changed.

Mutating Primitives does not work. When you assign a primitive value to a variable, the variable holds a copy of the value, not a reference to the value. Therefore, if you reassign the variable to a new value, it does not affect the original value.

While primitives themselves are immutable, variables assigned primitive values can still be reassigned to new values.

```js
let str = "foo";
let str2 = str;
str = "bar";
console.log(str); // "bar"
console.log(str2); // "foo"
```

`str` is initially assigned the value `"foo"`, and then `str2` is assigned the value of str. However, when `str` is reassigned to the value `"bar"`, it does not affect the value of `str2`. This is because `str` and `str2` hold separate copies of the original string value.

```js
str = "bar";
str.foo = 1;
str.foo // undefined
```

`str` is a primitive string value. When you assign `1` to `str.foo`, JavaScript creates an ephemeral object for the string `"bar"`, adds the property foo with the value `1`, and then discards the ephemeral object. Therefore, the assignment does not modify the original string value of `str`. When you then try to access `str.foo`, JavaScript creates a new ephemeral object for the string `"bar"`, but since the previous ephemeral object was discarded, the property `foo` does not exist on the new object, and therefore returns `undefined`

### Links
- [Primitive](https://developer.mozilla.org/en-US/docs/Glossary/Primitive)
- [Data structures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)
- [Primitive data type](https://en.wikipedia.org/wiki/Primitive_data_type)
