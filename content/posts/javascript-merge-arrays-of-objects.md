---
id: javascript-merge-arrays-of-objects
title: JavaScript - Merge Arrays of Objects
date: 2016-08-15T08:55:46+05:30
draft: false
categories:
- "javascript"
tags:
- "javascript"
- "arrays"
- "objects"
- "merge"
---

### Combine an array of objects
There are several ways to merge an array of objects in JavaScript:
__`Array.concat()` method__: This method returns a new array that is the concatenation of the original array and the elements or arrays passed as arguments.
```javascript
let arr1 = [{ a: 1 }, { b: 2 }];
let arr2 = [{ c: 3 }, { d: 4 }];
let mergedArr = arr1.concat(arr2);
console.log(mergedArr); // [{ a: 1 }, { b: 2 }, { c: 3 }, { d: 4 }]
```
__Spread operator__: The spread operator (...) can be used to spread the elements of an array into a new array, or to merge multiple arrays into a single array.
```javascript
let arr1 = [{ a: 1 }, { b: 2 }];
let arr2 = [{ c: 3 }, { d: 4 }];
let mergedArr = [...arr1, ...arr2];
console.log(mergedArr); // [{ a: 1 }, { b: 2 }, { c: 3 }, { d: 4 }]
```
__`Array.push()` method__: This method adds one or more elements to the end of an array and returns the new length of the array.
let arr1 = [{ a: 1 }, { b: 2 }];
let arr2 = [{ c: 3 }, { d: 4 }];
arr1.push(...arr2);
console.log(arr1); // [{ a: 1 }, { b: 2 }, { c: 3 }, { d: 4 }]
__`Array.reduce()` method__: This method applies a function to each element of an array and accumulates the results in a single value.
```javascript
let arr1 = [{ a: 1 }, { b: 2 }];
let arr2 = [{ c: 3 }, { d: 4 }];
let mergedArr = arr1.concat(arr2).reduce((acc, cur) => {
  acc.push(cur);
  return acc;
}, []);
console.log(mergedArr); // [{ a: 1 }, { b: 2 }, { c: 3 }, { d: 4 }]
```
__Lodash library__: Lodash is a JavaScript library that provides a variety of utility functions, including functions for merging arrays. The _.concat() function can be used to merge multiple arrays into a single array.
```javascript
let arr1 = [{ a: 1 }, { b: 2 }];
let arr2 = [{ c: 3 }, { d: 4 }];
let mergedArr = _.concat(arr1, arr2);
console.log(mergedArr); // [{ a: 1 }, { b: 2 }, { c: 3 }, { d: 4 }]
```
All of the above methods will merge the elements of the arrays and will not change the original arrays. However, it's worth noting that if the elements of one array have the same key as elements of another array, the value of that key in the final array will be the value of the second array's element.
### Combine an array of objects by a key
To combine an array of objects by a key, you can use the Array.reduce() method to iterate through the array and create a new object that groups the objects by their key value.
Here's an example of how to combine an array of objects by a key:
```javascript
let arr = [{ id: 1, name: "John" }, { id: 2, name: "Mike" }, { id: 1, age: 30 }, { id: 2, age: 25 }];
let grouped = arr.reduce((acc, cur) => {
    if (!acc[cur.id]) {
        acc[cur.id] = { id: cur.id };
    }
    Object.assign(acc[cur.id], cur);
    return acc;
}, {});
console.log(grouped);
// Outputs: { 
// 1: { id: 1, name: "John", age: 30 }, 
// 2: { id: 2, name: "Mike", age: 25 } }
```
In this example, the function uses the reduce() method to iterate through the array of objects, and for each object it checks if an object with the same id already exists in the accumulator object. If it doesn't exist, it creates a new object with the current object's id as the key. After that, it uses the Object.assign() method to merge the current object with the object in the accumulator object with the same key.
You can also use the Lodash library's `_.groupBy()` function to achieve the same result:
```javascript
let grouped = _.groupBy(arr, 'id');
console.log(grouped);
// Outputs: 
// { 1: [ { id: 1, name: "John" }, { id: 1, age: 30 } ], 
// 2: [ { id: 2, name: "Mike" }, { id: 2, age: 25 } ] }
```
In this example, _.groupBy() function takes an array and the key by which you want to group the objects, in this case it's 'id', and it returns an object that groups the objects by their key value.
It's worth noting that the above two examples will give you an object with grouped objects, but the original array will remain unchanged.
### Combine several array of objects
To combine multiple arrays of objects, you can use the Array.concat() method to join all the arrays into a single array, and then use the Array.reduce() method or Lodash's _.groupBy() function to group the objects by a specific key.
Here's an example of how to combine multiple arrays of objects using the Array.concat() method:
```javascript
let arr1 = [{ id: 1, name: "John" }, { id: 2, name: "Mike" }];
let arr2 = [{ id: 1, age: 30 }, { id: 2, age: 25 }];
let arr3 = [{ id: 1, city: "New York" }, { id: 2, city: "Los Angeles" }];
let combinedArr = arr1.concat(arr2, arr3);
let grouped = combinedArr.reduce((acc, cur) => {
    if (!acc[cur.id]) {
        acc[cur.id] = { id: cur.id };
    }
    Object.assign(acc[cur.id], cur);
    return acc;
}, {});
console.log(grouped);
// Outputs: { 
// 1: { id: 1, name: "John", age: 30, city: "New York" }, 
// 2: { id: 2, name: "Mike", age: 25, city: "Los Angeles" } }
```
In this example, the function uses the `Array.concat()` method to join the arrays arr1, arr2, and arr3 into a single array `combinedArr`. After that, it uses the reduce() method to iterate through the combined array of objects, and for each object it checks if an object with the same id already exists in the accumulator object. If it doesn't exist, it creates a new object with the current object's id as the key. After that, it uses the Object.assign() method to merge the current object with the object in the accumulator object with the same key.
Alternatively, you can use lodash's `_.concat()` function to join the arrays and _.groupBy() function to group the objects by a specific key:
```javascript
let combinedArr = _.concat(arr1, arr2, arr3);
let grouped = _.groupBy(combinedArr, 'id');
console.log(grouped);
// Outputs: { 
// 1: [ { id: 1, name: "John" }, { id: 1, age: 30 }, { id: 1, city: "New York" } ], 
// 2: [ { id: 2, name: "Mike" }, { id: 2, age: 25 }, { id: 2, city: "Los Angeles" } ] }
```
In this example, _.concat() function joins the arrays arr1, arr2, and arr3 into a single array combinedArr and _.groupBy() function takes an array and the key by which you want to group the objects, in this case it's 'id', and it returns an object that groups the objects by their key value.
### Links
- [Merge two arrays of objects, StackOverflow](https://stackoverflow.com/questions/7146217/merge-2-arrays-of-objects)

