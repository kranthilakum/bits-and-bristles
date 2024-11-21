---
title: JavaScript snippets 001
date: 2018-08-17T09:55:46+05:30
draft: false
categories:
- "javascript"
tags:
- "javascript"
- "snippets"
---

### 0001 : Get all images from a webpage

```js
const getImages = (el, includeDuplicates=false) => {
    const images = [...el.getElementsByTagName('img')].map(img => img.getAttribute('src'));
    return includeDuplicates ? images : [...new Set(images)]
}

const images = getImages(window.document);
```

[Source](https://www.30secondsofcode.org/js/s/get-images/)

----

### 0002 : Get all links from a webpage

----

### 0003 : Get the time in HH:MM:SS format from a Date object
```js
new Date().toTimeString().slice(0,8)
'00:32:39'
```

[Source](https://www.30secondsofcode.org/js/s/get-colon-time-from-date/)

---

### 0004 : Display current date in YYYY-MM-DD format

```js
new Date().toISOString().slice(0,10)
'2024-06-06'
```

-----

### 0005 : Change the sign of a number

```js
const negate = num => -num;

negate(42) // -42

negate(-42) // 42
```

-----

### 0006 : Copy the sign from another value

Compare the signs of the two numbers (source and target). If they have the same sign, return the target number. If they have different signs, return the negation of the target number.

```js
const copySign = (source, target) => {
    return Math.sign(source) === Math.sign(target) ? target : -target;
}
```

```js
const copySign = (source, target) => {
    return Math.abs(target) * Math.sign(source);
}
```

`Math.sign` returns either 1 (positive), 0 (zero), or -1 (negative) depending on the sign of the number.

- [Source](https://www.30secondsofcode.org/js/s/copy-sign-to-number/)
- [Math.sign](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/sign)
- [Unary negation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Unary_negation)

-----

### 0007 : Get the time from a date

```js
```

-----

### 0008 : Leap year check

Get 29th February of current year and check if it is a month of February.

```js
const isLeapYear = year => new Date(year, 1, 29).getMonth() === 1;

isLeapYear(2020) // true
isLeapYear(2024) // true
isLeapYear(2100) // false
```

Check if the year is divisible by 4 and not divisible by 100 or divisible by 400.

```js
const isLeapYear = year => (year % 4 === 0 && year % 100 !== 0) || year % 400 === 0;

isLeapYear(2020) // true
isLeapYear(2024) // true
isLeapYear(2100) // false
```

[Source](https://www.30secondsofcode.org/js/s/is-leap-year/)
