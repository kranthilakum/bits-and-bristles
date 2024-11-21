---
title: JavaScript type system
date: 2018-08-13T08:55:46+05:30
draft: true
categories:
- "javascript"
tags:
- "javascript"
- "primitive"
- "types"
- "datatypes"
---

A value is a specific piece of data that has a _type and a value_, while a variable is a named container that can _hold a value_.

In other words, a variable is a label that can be used to _refer to a value_, but the variable itself does not have a type or a value.

For example, in the JavaScript code `let x = 5;`, `x` is a variable and `5` is a value. The value `5` has a type of `number`, while the variable `x` does not have a type. Instead, the variable `x` can hold a value of any type, and in this case, it is holding a value of type `number`.

> The type of a value is determined by the value itself, not by the variable that holds it.

For example, in the code `let x = 5; let y = "hello";`, the variable `x` has a value of type `number`, while the variable `y` has a value of type `string`. However, the types of the variables `x` and `y` are not explicitly declared and can be changed at any time.

JavaScript is a dynamically typed language, which means that the type of a value is __determined at runtime based on the value itself__. This is in contrast to statically typed languages like Java or C++, where the type of a variable is explicitly declared and cannot be changed.

