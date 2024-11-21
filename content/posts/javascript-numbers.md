---
title: JavaScript numbers
date: 2018-08-13T09:55:46+05:30
draft: false
categories:
- "javascript"
tags:
- "javascript"
- "numbers"
---

### Using post-increment and pre-increment operators with a variable

We have a variable `number` that is initially set to `0`. We then use the post-increment operator (`number++`) and the pre-increment operator (`++number`) to modify its value.

```js
let number = 0;
console.log(number++, ++number, number); // Output: 0 2 2
```

The post-increment operator increments the variable after returning its current value.

```js
let number = 0;
console.log(number++); // Output: 0
console.log(number); // Output: 1
```

The pre-increment operator increments the variable before returning its new value.

```js
let number = 0;
console.log(++number); // Output: 1
console.log(number); // Output: 1
```

In this case, the output is `0 2 2` because the first log statement outputs the current value of `number` (which is `0`), the second log statement increments `number` to `1` and then outputs its new value, and the third log statement simply outputs the current value of `number` (which is `2`).

-----

### Comparing variables with the `==` and `===` operators

We have three variables `a`, `b`, and `c`, all initialized to the value `3`. We then compare them using the `==` (loose equals) and `===` (strict equals) operators.

```js
let a = 3, b = new Number(3), c = 3;
console.log(a == b, b === c, a.toString() == b.toString()); // Output: true false true
```

`a` and `c` are primitive values, while `b` is an object created using the `new Number()` constructor. 

The `==` operator compares the values of `a` and `b` and returns `true` because `==` performs type coercion and converts the operands to the same type before comparing them.

The `===` operator compares the values and types of `b` and `c` and returns `false` because `===` does not perform type coercion. It checks if the operands are of the same type and have the same value. Here `b` is an object and `c` is a primitive value, so they are not strictly equal.

The last comparison uses the `toString()` method to convert `a` and `b` to strings before comparing them. Since both `a` and `b` are converted to the same type (string) before comparison, the result is `true`.

-----

### Using `isNaN()` function to check if a value is not a number

Let's use the `isNaN()` function to check if a given expression is not a number. The expression can be a number, a string, a boolean, or `null`.

```js
console.log(isNaN(5.2 + 2), isNaN(parseInt('a')), isNaN(true * 2), isNaN(null + 1)); // Output: false true false false
```
The `isNaN()` function returns true if the argument is not a number, and false otherwise. In this case, the first expression evaluates to a number (`7.2`), so `isNaN()` returns `false`. The second expression evaluates to a `NaN`, so `isNaN()` returns true. The third expression `true * 2` evaluates to 2, which is a number, because `true` is converted to `1` when used in a numeric context. Similarly, `null + 1` evaluates to `1`, which is a number, because `null` is converted to `0` when used in a numeric context.

-----

### Using the toString() method to convert a number to a string

We have a number num and we want to convert it to a string using the toString() method. However, we need to be careful when using this method because it can throw a TypeError if the this value is not a number.

To avoid this error, we can use the Number() function to ensure that the this value is a number before calling the toString() method.

```js
let num = 123;
console.log(num.toString(), Number(456).toString(), (789).toString()); // Output: "123" "456" "789"
```

In this example, we call the toString() method on num and Number(456) to ensure that the this value is a number. We can also call it on (789) because the parentheses ensure that the value is treated as a number.

-----

### Using the toString() method with a radix argument

We have a number num and we want to convert it to a string using the toString() method with a radix argument. The radix argument specifies the base of the number system to use when converting the number to a string.

```js
let num = 255;
console.log(num.toString(16), num.toString(2)); // Output: "ff" "11111111"
```

We call the toString() method on num with a radix argument of 16 to convert the number to a hexadecimal string. We also call it with a radix argument of 2 to convert the number to a binary string.

Note that if the radix argument is not specified, the toString() method uses a radix of 10 (decimal) by default.

-----

### Using the toFixed() method to format a number with a fixed number of decimal places

We have a number num and we want to format it with a fixed number of decimal places using the toFixed() method. The toFixed() method returns a string representing the number with a specified number of decimal places.

```js
let num = 123.456;
console.log(num.toFixed(0), num.toFixed(2), num.toFixed(5)); // Output: "123" "123.46" "123.45600"
```

In this example, we call the toFixed() method on num with different arguments to format the number with 0, 2, and 5 decimal places, respectively.
