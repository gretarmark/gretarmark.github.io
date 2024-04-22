---
layout: post
title: Linked Lists
published: true
---

Linked lists are a collection of nodes where each node contains data and a pointer to the next node.
Linked lists are always created in the heap, not in the stack. On the other hand, arrays can be created both on the heap and the stack.
Linked lists are more dynamical than arrays, it's easy to increase or reduce the size of it.
The beginning of a linked list is a pointer which is usually called "first" or "head". The pointer "first" points to the first node (or the header node) in the linked list.
In an array, all the addresses are contiguous, which means that they are side by side. But in linked lists, the addresses of each node are not necessarily side by side, they can be everywhere.

## Defining a node

There are two things to consider when defining a node. In each node there are "data" and a "pointer".
Data may be any type, like integer, float, double or any other type. On the other hand, pointer is a specific type, the pointer is pointing to a node and therefore
a pointer is a node type. Node is a pointer of its own type.

Nodes contains two members

* data (let's call it data)
* pointer (let's call it next)

Node structure is having data and a pointer to the next node.

In C language we can define a node structure using "struct" in C and its members are data and next:

```C
Struct Node
{
    int             data;  //Can be any type e.g. float, double... integer is easiest to work with
    Struct Node     *next; //Must be of its own type, "node"
};
``` 
A structure like above is called self-referential structure and are used in linked lists.
For C programming language we use a struct, but in C++ we use a class.
The difference between a class and a struct is that in classes, everything by default is private and in struct, everything is by default public.
In C++ you can actually use either struct or class but in C you can only use struct.

Let's assume that the integer type value "data" always takes 2 bytes because it's an integer.
And the struct node type value pointer "*next" will also take 2 bytes because it's going to point on integers.
Each node will therefore take 4 bytes. If the first byte address in a node is 300, then the next byte in it is 301, then 302 and finally, 303.
But for pointers we only need the first byte address which would be 300.

To create a node, we need first of all a pointer, because nodes have to be created inside the heap. 
But the first pointer will always be created on the stack, the rest will be inside the heap.
Let's create a node:

```C
struct node *p; //This pointer is created on the stack
``` 

Next we will create a node on the heap:

```C
p = (Struct Node*)malloc(sizeof(Struct Node)); //In C we use memory allocation function. We also need the size of the node which is 4.
                                 //We can also just use the sizeof() function 
```

In C++ we would just write p = new Node; instead of p = (Struct Node*)malloc(sizeof(Struct Node));. The word "new" in C++ will create a node on the heap.








