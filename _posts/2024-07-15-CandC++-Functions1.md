---
layout: post
title: Parameter Passing in C and C++
published: true
---

When writing functions in C and C++, we often need to pass information into the function to perform specific tasks.
This process is known as parameter passing.

In this post, I will explain how parameters are passed into functions in both C and C++, and the different ways of doing so.
We will cover three methods of parameter passing:

1. **Pass by Value (C and C++)** 
2. **Pass by Address (C and C++)** 
3. **Pass by Reference (C++ only)** 

# Parameter vs. Argument

Before diving into the methods, let's clear up two commonly confused terms:

* **Parameter:** The variable listed in the function's definition.
* **Argument:** The actual value or variable passed to the function when it's called.

Now, let's explore the three ways you can pass parameters to a function.

<!-- --- -->

# 1. Pass by Value (C/C++)

In the **pass by value** method, the function receives a copy of the actual values (arguments) passed in.
This means the original variables remain unchanged, even if the function modifies its own local copies.

Let's look at an example:
    
```{C++}
// Pass by Value
#include <stdio.h>

void swap(int x, int y);

int main() {
    
    int a = 15, b = 20;

    printf("a1 = %d \n",a);
    printf("b1 = %d \n",b);

    swap(a,b);

    printf("a2 = %d \n",a);
    printf("b2 = %d",b);

    return 0;
}

void swap(int x, int y)
{
    int temp;
    temp = x;
    x = y;
    y = temp;
}
```
**Code 1: Pass by value in C.**

**Explanation:**
* In this code, the **swap()** function attempts to swap the values of **a** and **b**.
However, since the values of **a** and **b** are passed by value (i.e., only copies are passed), 
the original variables in **main()** remain unchanged.

**When to use pass by value:**
* Use pass by value when you do not need to modify the original variables and only require the function to be operate on copies of them.

# 2. Pass by Address (C/C++)

In pass by address, you pass the memory addresses of the variables instead of their values. 
The function can then directly modify the original variables because it has access to their addresses via pointers.

Here's an example:

```{C}
// Pass by Address

#include <stdio.h>

void swap(int * x, int * y);

int main() {
    
    int a = 15, b = 20;

    printf("a1 = %d \n",a);
    printf("b1 = %d \n",b);

    swap(&a,&b);

    printf("a2 = %d \n",a);
    printf("b2 = %d",b);

    return 0;
}

void swap(int * x, int * y)
{
    int temp;

    temp = *x;
    *x = *y;
    *y = temp;
}
```
**Code 2: Pass by address in C.**

**Explanation:**
* The **swap()** function now uses pointers (int *x and int *y). This allows it to directly modify the values of **a** and **b**
through their memory addresses. As a result, the values of **a** and **b** are successfully swapped in **main()**.

**Key Concepts:**
* The **&** operator retrieves the address of a variable.
* The * operator dereferences the pointer, allowing access to the value stored at the address.

**When to use pass by address:**
* Use pass by address when you want the function to modify the original variables or when passing large data structures like arrays (to avoid copying).

# 3. Pass by Reference (C++ Only)

**Pass by reference** is a feature unique to C++. It allows a function to directly operate on the original variables without needing pointers.
Instead of passing the memory address, we pass references, which act as **aliases** for the original variables.

Here's how it works:

```{C++}
// Pass by reference

#include <stdio.h>

void swap(int & x, int & y);

int main() {
    
    int a = 15, b = 20;

    printf("a1 = %d \n",a);
    printf("b1 = %d \n",b);

    swap(a,b);

    printf("a2 = %d \n",a);
    printf("b2 = %d",b);

    return 0;
}

void swap(int & x, int & y)
{
    int temp;

    temp = x;
    x = y;
    y = temp;
}
```
**Code 3: Pass by reference in C++.**

**Explanation:**
* In this case, the function parameters **int &x** and **int &y** are references to the original variables **a** and **b**.
Since **x** and **y** are just nicknames for **a** and **b**, any changes made to **x** and **y** are directly reflected in the original variables.

**Advantages of pass by reference:**
* It allows you to modify the original variables without using pointers.
* It's more readable and avoids the syntax complexities of pointers.

**When to use pass by reference:**
* Use pass by reference when you need to modify the originaly variables in C++, especially when working with
large data structures or when you want a cleaner syntax than pointers.

# Summary

* **Pass by value:** A copy of the original data is passed to the function. The original data is not modified.
* **Pass by address:** The function recieves the address of the original data and can modify it via pointers.
* **Pass by reference (C++ only):** The function receives references (aliases) to the original data,
allowing direct modification with cleaner syntax.



