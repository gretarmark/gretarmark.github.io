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

## Parameter vs. Argument

Before diving into the methods, let's clear up two commonly confused terms:

* **Parameter:** The variable listed in the function's definition.
* **Argument:** The actual value or variable passed to the function when it's called.

Now, let's explore the three ways you can pass parameters to a function.

---

## 1. Pass by Value (C/C++)

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

---

## 2. Pass by Address (C/C++)

In pass by address, you pass the memory addresses of the variables instead of their values. 
The function can then directly modify the original variables because it has access to their addresses via pointers.

Here's an example:

```{C}
// Pass by Address

#include <stdio.h>

void swap(int * x, int * y);

int main() {
    
    int a,b;

    a = 15;
    b = 20;

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
* The ***** operator dereferences the pointer, allowing access to the value stored at the address.

* BLA

When a function is 'passed by address,' the addresses of the actual parameters are passed to the formal parameters, and these formal parameters must be pointers. Any modifications made inside the function will directly affect the values of the actual parameters.

Dereferencing of the pointers is performed within the function by changing the values from x and y to \*x and \*y:

* '&' represents an address.
* '\*' denotes a pointer.
* Pointers exclusively hold addresses.

The output from code 2 below is as follows:

* a1 = 15
* b1 = 20
* a2 = 20
* b2 = 15

The **swap()** function effectively swaps the values of a and b.



---

## Pass by Reference

Call or pass by reference is a powerful mechanism in C++ that is not part of the C language. In this paradigm, references serve as 'nicknames' for variables. For instance, if &x is a reference to a, and &y is a reference to b, then a is effectively x, and b is y.

References do not consume additional memory; they are aliases for existing variables. In the main function, variables are named a and b, while the swap function refers to them as x and y. The manipulation occurs on the formal parameters x and y, modifying the actual parameters a and b.

Although functions typically cannot access variables from other functions directly, call by reference allows the swap function to become part of the main function. This is distinct from 'pass by value' and 'pass by address,' where the swap function remains a separate entity.

In practice, the machine code of the swap function is inserted directly into the main function, akin to a monolithic program. It's essential to note that call by reference is not always recommended, especially for heavy functions. It should be used judiciously, and other commonly used features, such as call by value and call by address, might be more suitable for certain scenarios.

The output from code 3 below is as follows:

* a1 = 15
* b1 = 20
* a2 = 20
* b2 = 15

Again, the **swap()** function effectively swaps the values of a and b.

```{C++}
// Pass by reference

#include <stdio.h>

void swap(int & x, int & y);

int main() {
    
    int a,b;

    a = 15;
    b = 20;

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

---

