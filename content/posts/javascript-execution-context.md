---
title: JavaScript execution context
date: 2018-08-16T09:55:46+05:30
draft: false
categories:
- "javascript"
tags:
- "javascript"
- "execution context"
- "event loop"
- "macro task"
- "micro task"
---

### Event Loop Overview

The event loop is a fundamental concept in JavaScript that ensures non-blocking execution. It coordinates how asynchronous operations, like timers, promises, and callbacks are executed.

### Concepts

In JavaScript, the call stack is a data structure that keeps track of the functions that the program is calling. When a function is called, it's added (pushed) to the call stack. When it finishes executing, it's removed (popped) from the call stack.

The event loop is responsible for checking the call stack and task queues to determine which function to execute next. It follows a specific order to handle different types of tasks.

In addition to the call stack, JavaScript has two main task queues:

- __Macrotask Queue__: contains a list of tasks like setTimeout, setInterval, and I/O operations.
- __Microtask Queue__: contains a list tasks like Promises and queueMicrotask.

The event loop processes microtasks before macrotasks. This ensures that microtasks are executed before the next macrotask, providing a more predictable order of execution.

-----

#### Basic Example

```js
console.log(1);

function myFunction() {
  console.log(2);
}

myFunction();
console.log(3);
```

Explanation:

- The above script runs synchronously. The call stack handles the function calls one by one.
- `console.log(1)` is added to the call stack, called, and removed from the call stack.
- `myFunction()` is added to the call stack, called, and within `myFunction`, `console.log(2)` is executed, and then `myFunction` is popped off from the call stack.
- Finally, `console.log(3)` is added to the call stack, called, and removed from the call stack.

### setTimeout and Macrotasks

`setTimeout` is part of the Web APIs and allows us to schedule callback functions to be executed after a specified delay.

It adds a macrotask to the task queue.

It is important to note that the callback function is not executed immediately after the specified delay. Instead, it is added to the task queue and executed when the call stack is empty.

```js
console.log(‘Start’);

setTimeout(() => {
  console.log(‘Timeout’);
}, 0);

console.log(‘End’);
```

Explanation:
- console.log('Start') runs first.
- setTimeout schedules a callback to be executed after 0 milliseconds delay. The callback is added to the macrotask queue.
- console.log('End') is executed next.
- After the call stack is empty, the event loop checks the macrotask queue and executes the console.log('Timeout').

### Microtasks (Promises, queueMicrotask)

Microtasks are executed before macrotasks. Promises and queueMicrotask are two main ways to create microtasks.

```js
console.log(‘Start’);

setTimeout(() => {
  console.log(‘setTimeout’);
}, 0);

Promise.resolve().then(() => {
  console.log(‘Promise’);
});

console.log(‘End’);
```

Explanation:
- console.log('Start') runs first.
- setTimeout schedules a macrotask.
- Promise.resolve().then schedules a microtask.
- console.log('End') runs next.
- The microtask (Promise callback) runs before the macrotask (setTimeout callback).

### Execution Order Example

Consider this example involving different types of tasks:

```js
console.log(‘Script Start’);

setTimeout(() => {
  console.log(‘Timeout 1’);
}, 0);

Promise.resolve().then(() => {
  console.log(‘Promise 1’);
}).then(() => {
  console.log(‘Promise 2’);
});

setTimeout(() => {
  console.log(‘Timeout 2’);
}, 0);

console.log(‘Script End’);
```

Explanation:
1. console.log('Script Start')
2. setTimeout schedules Timeout 1
3. Promise schedules Promise 1 and then Promise 2
4. setTimeout schedules Timeout 2
5. console.log('Script End')
6. Event loop processes microtasks: Promise 1, Promise 2
7. Event loop processes macrotasks: Timeout 1, Timeout 2

Output:
Script Start
Script End
Promise 1
Promise 2
Timeout 1
Timeout 2

### Understanding Async Functions

Async functions allow writing asynchronous code in a synchronous manner using await.

```js
async function asyncFunction() {
  console.log(‘Async start’);
  await new Promise(resolve => setTimeout(resolve, 1000));
  console.log(‘Async end’);
}

console.log(‘Before async’);
asyncFunction();
console.log(‘After async’);
```

Explanation:
- console.log('Before async')
- asyncFunction logs Async start.
- The await causes the function to pause, and the rest of the function is pushed to the microtask queue.
- console.log('After async')
- After 1 second, the async function continues, logging Async end.

### Complex Example with Microtasks and Macrotasks

Let’s examine a more complex scenario:

```js
async function firstFunction() {
  console.log(‘1’);
  await secondFunction();
  console.log(‘2’);
}

async function secondFunction() {
  console.log(‘3’);
  return new Promise(resolve => {
    console.log(‘4’);
    resolve();
  });
}

console.log(‘A’);
firstFunction();
console.log(‘B’);

setTimeout(() => {
  console.log(‘C’);
}, 0);

Promise.resolve().then(() => {
  console.log(‘D’);
});
```

Explanation:
1. console.log('A')
2. firstFunction is called.
- Logs 1.
- Calls secondFunction.
- Logs 3.
- Immediately logs 4 (before resolving the promise).
- Execution pauses at await.
3. console.log('B')
4. Schedules macrotask: setTimeout for C.
5. Schedules microtask: Promise for D.
6. Executes microtask: Logs D.
7. Resumes firstFunction: Logs 2.
8. Executes macrotask: Logs C.

Output:

A
1
3
4
B
D
2
C

### Summary and Best Practices

- Call Stack: Executes function calls.
- Macrotasks: Scheduled using setTimeout, setInterval, etc.
- Microtasks: Scheduled via Promises, queueMicrotask.
- Execution Order: Microtasks are executed before macrotasks.

Best Practices:

- Avoid nesting excessive async functions to prevent complexity.
- Understand the difference between synchronous and asynchronous operations.
- Use Promises and async/await wisely to manage complex asynchronous code.

By understanding the event loop and task queues, you can write more efficient and predictable asynchronous JavaScript.
