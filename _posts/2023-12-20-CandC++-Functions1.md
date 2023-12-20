---
layout: post
title: Parameter Passing in C and C++
published: true
---

Today I am going to talk about how to pass information into a function in C and C++.

There are two types of informations that are passed into a function:
* A parameter: The variable listed inside the parentheses in the function definition.
* An argument: The value that is sent to the function when it is called.

There are two parameter passing methods in C but three methods in C++:
1. Pass by value (C/C++)
2. Pass by address (C/C++)
3. Pass by reference (only in C++)

---

## Pass by Value
When the code below is compiled, the output is

* a1 = 15
* b1 = 15
* a2 = 15
* b2 = 15

This means that the actual parameters a and b that were passed into the swap() function were actually not swapped. 
What really happened is that the parameters x and y were assigned the values of a and b, so inside the function, the values became

* x = 15
* y = 15

and x and y were swapped inside of the function, but these values were never returned from the function so they kind of died after the function finished compiling and a and b in the main() function still had the same value as before.

"Pass by value" is used when you don't have to modify the actual parameters that you pass into your function and you only need to return some result, for example when doing addition and similar things. Swap function is a an example of a function that is not suppose to be written using "pass by value". 
    
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



---

## Pass by Address

When "passed by address", the addresses of the actual parameters are passed to the formal parameters of a function and the formal parameters must be pointers.
Any changes that are made inside of the function will modify the actual parameters.

The Dereferencing of the pointers is made inside of the function by changing the values from x and y to \*x and \*y. 

* & is an address
* \* is a pointer
* Pointers can only take addresses

The output from the code below is
* a1 = 15
* b1 = 20
* a2 = 20
* b2 = 15

The swap() function now swaps the values of a and b.

```{C++}
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

---

## Pass by Reference

Call or pass by reference is only supported in C++. This is not a part of the C language. This is very powerful mechanism of C++. 

In this case, &x is a reference to a, and &y is a reference to b. Reference is nothing else than "a nickname" for a variable, so a is x and b is y.  

References do not take any memory. The existing variables are used but they are simply given another name. The main function is naming the variables a and b, but the swap function is naming them x and y. The formal variables x and y are manipulated and the actual parameters a and b are modified.

One fact is that a function cannot access the variables of another function directly, it can access indirectly. Now we can ask us, how can the swap function then access the parameters a and b in the main function directly when using "pass by reference"? In this case, the swap function becomes part of the main function which is not the case with "pass by value" and "pass by address".
The machine code of the swap function is simply pasted into the main function, so this is similar to monolithic program, the entire code is inside the single main function. The machince code is monolithic though the source code is procedural or modular. Call by reference is not recommended to use for heavy functions, just for small ones, it should be used carefully and cannot be used always. More commonly used features are call by value and call by address.

```C++
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


