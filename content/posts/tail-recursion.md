---
title: "Tail Recursion"
date: 2020-09-10T09:55:46+05:30
draft: false
categories:
- "programming"
tags:
- "programming"
- "recursion"
- "tail-recursion"
---

In a tail recursive function, there are no pending operations to be performed on return from a recursive call. Assume two identical/non-identical functions, `f(x)` and `g(x)`. A call to the function `f(x)` in the body of function `g(x)` is called a tail call, if `g(x)` returns the result of calling `f(x)` without any further computation.


For example, look at the following pseudo-code

```
if x = 0 then
    return f(x)
else
    return 2*f(x)
```

The first call to function `f(x)` in the body of `g(x)` is a tail call, as the return value of function `g(x)` is exactly the return value of the call to `f(x)`. The second call to function `f(x)` in the body of `g(x)` is not a tail call because `g(x)` performs a computation involving the return value of `f(x)` before `g(x)` returns.


A function `f(x)` is tail recursive if all recursive calls in the body of `f(x)` are calls to function `f(x)`.

```
/* Non-tail recursive factorial function */
#include
int fact_comp(int);
void main()
{
    int num, fact;
    printf(“Enter number: t“);
    scanf(“%d”, &num);
    fact = fact_comp(num);
    printf(“Result: %d”, fact);
}
int fact_comp(int n)
{
    if(n==1)
        return 1;
    else
        return n * fact_comp(n–1);
}
```

```
/* Tail recursive factorial function */
#include
int fact_comp(int, int);
void main()
{
    int num, fact;
    printf(“Enter number: t“);
    scanf(“%d”, &num);
    fact = fact_comp(num,1);
    printf(“Result: %d”, fact);
}
int fact_comp(int n, int r)
{
    if(n==1)
        return r;
    else
        return fact_comp(n–1, n * r);
}
```

Tail recursion is desirable because it eliminates the need to store the result of the computations made in a function before making the tail recursive function call. The result of the computations made before tail recursive function call is passed as an argument to the tail recursive function. Due to this, conversion of a non-tail recursive function to a tail recursive function is often required.

#### Convert a non-Tail Recursive Function to a Tail Function

A non-tail recursive function can be converted to a tail recursive function by adding one or more auxiliary parameters. Incorporate the pending operation into auxiliary parameter in such a way that the non-tail recursive function no longer has a pending operation.
