---
title: JavaScript miscellaneous questions 001
date: 2018-08-15T09:55:46+05:30
draft: false
categories:
- "javascript"
tags:
- "javascript"
- "questions"
---

### Section 1: Working with Maps

Question: Which method will return the value “Hello World”?

Given a function and a Map where a function is set as a key, you can retrieve the value using the reference of the function.

```js
// Defining a function
function myFunc() {
  return “Hello World”;
}

// Creating a Map
const myMap = new Map();

// Setting the function as a key in the Map
myMap.set(myFunc, “Hello World”);

// Retrieving the value using get method with myFunc as key
console.log(myMap.get(myFunc)); // Output: “Hello World”

// Using another variable as reference to the same function
const anotherVariable = myFunc;
console.log(myMap.get(anotherVariable)); // Output: “Hello World”
```


### Section 2: Freezing Objects and Proxies

Question: What does the person object look like after executing the script with Object.freeze and Proxy?

```js
// Creating a person object
const person = {
  name: “Jane”,
  address: {
    city: “Amsterdam”
  }
};

// Freezing the person object
Object.freeze(person);

// Creating a Proxy for the person object
const personProxy = new Proxy(person, {
  set(target, key, value) {
    target[key] = value;
    return true;
  }
});

// Attempting to change properties via proxy
personProxy.name = “Sarah”; // Won’t change as ‘name’ is frozen
personProxy.address.city = “Paris”; // Will change as freeze is shallow

// Logging the person object
console.log(person); // Output: { name: “Jane”, address: { city: “Paris” } }
```


### Section 3: Using Strict Mode with Frozen Objects

Question: How does use strict affect modifications to frozen objects?

```js
'use strict'; // Enabling strict mode

const nameObj = {
  name: “John”
};

Object.freeze(nameObj);

try {
  nameObj.name = “Jane”; // Throws TypeError in strict mode
} catch (error) {
  console.error(error); // Output: TypeError: Cannot assign to read only property ‘name’ of object ‘#<Object>’
}
```


### Section 4: Useful Array Methods

Question: How does slicing, splicing, and deleting elements in arrays affect the array?

```js
let array = [1, 2, 3, 4, 5];

// Splice modifies the original array
array.splice(2, 3); // Removes elements from index 2, removes [3, 4, 5], resulting in [1, 2]
console.log(array); // Output: [1, 2]

// Concat returns a new array
let newArray = array.concat([6]);
console.log(newArray); // Output: [1, 2, 6]
console.log(array); // Output: [1, 2]

// Slice returns a subset of the array
let slicedArray = array.slice(1);
console.log(slicedArray); // Output: [2]
console.log(array); // Output: [1, 2]

// Delete creates an empty slot
delete array[0];
console.log(array); // Output: [ <1 empty item>, 2 ]
console.log(array.length); // Output: 2
```

### Section 5: Using Symbol in JavaScript

Question: How does the global symbol registry and local symbol creation differ?

```js
let symbolOne = Symbol.for(“key”);
let symbolTwo = Symbol(“key”);
let symbolThree = Symbol.for(“key”);

console.log(symbolOne === symbolTwo); // Output: false (Different memory references)
console.log(symbolOne === symbolThree); // Output: true (Same global symbol)
console.log(symbolTwo === symbol(“key”)); // Output: false (Unique symbols)
```

### Section 6: Tagged Template Literals

Question: How do tagged template literals work?

```js
function tag(strings, …values) {
  console.log(strings); // Array of strings
  console.log(values);  // Values of expressions
}

let greeting = “Hello”;
tag${greeting}, World!; 
// Output:
// [ “Hello”, “, World!” ]
// [ “Hello” ]
```

### Section 7: Default Parameters and Object Comparison

Question: How does using default parameters and spreading objects affect the comparison?

```js
function compareUsers(user1, user2 = user1) {
  return user1 === user2;
}

let user = { name: “John” };

console.log(compareUsers(user, { …user })); // false: Different object references
console.log(compareUsers(user)); // true: Same object reference as default
console.log(compareUsers({ …user }, { …user })); // false: Different object references
```
