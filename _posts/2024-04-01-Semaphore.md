---
layout: post
title: Semaphores
published: false
---

Semaphores are...

Semaphores can be used as mutexes to give exclusive access to a shared resource.
Mutex means Mutual Exclusive.
Semaphores are used as mutex in FreeRTOS and can be defined e.g. as

```C++
LEDMutex = xSemaphoreCreateMutex();
```

Usually you need one mutex per shared resource.
As soon as a task wants exclusivity, it takes the mutex.

<!-- 
* https://www.youtube.com/watch?v=684KSAvYbw4
-->

...Post in progress...
