---
layout: post
title: C++
published: true
---

C++ pointers programming challenges:

** Memory Leak

In the code snip below
  
```{C++}
int **arr;
arr = malloc(5 * sizeof(int *));
for (int i = 0; i < 5; i++) {
arr[i] = malloc(4 * sizeof(int));
}
free(arr);
```
