---
layout: post
title: Parameter Passing in C and C++
published: true
---

Today, I am going to discuss how to pass information into a function in C and C++.

Two types of information can be passed into a function:

* **A parameter:** The variable listed inside the parentheses in the function definition.
* **An argument:** The value sent to the function when it is called.

There are two parameter passing methods in C and three methods in C++:

1. **Pass by value (C/C++):** The actual value of the variable is passed to the function.
2. **Pass by address (C/C++):** The memory address of the variable is passed to the function.
3. **Pass by reference (only in C++):** A reference to the variable is passed to the function.

---

## Pass by Value
When code 1 below is executed, the output is as follows:

* a1 = 15
* b1 = 15
* a2 = 15
* b2 = 15

This indicates that the actual parameters a and b passed into the **swap()** function were not effectively swapped. What occurred is that the parameters x and y were assigned the values of a and b. Consequently, inside the function, the values became:

* x = 15
* y = 15

Although x and y were swapped within the function, these values were not returned, and they essentially 'died' after the function finished execution. As a result, a and b in the **main()** function retained their original values.

'Pass by value' is suitable when you don't need to modify the actual parameters in your function, and you only need to return a result, for example, in operations like addition. The swap function is an example of a function that is not meant to be implemented using 'pass by value'.
    
```{C++}
// Pass by Value
#include <stdio.h>

void swap(int x, int y);

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

void swap(int x, int y)
{
    int temp;
    temp = x;
    x = y;
    y = temp;
}
```
**Code 1: Pass by value in C.**

---

## Pass by Address

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

