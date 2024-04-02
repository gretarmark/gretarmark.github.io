---
layout: post
title: FreeRTOS - STM32
published: false
---

FreeRTOS can be used in STM32 projects using the STM32CubeIDE.

## Setup

To use FreeRTOS within a project do the following:

* Create project
* Go to middleware and software packs
* Under Interface, choose CMSIS_V1 (version 1 is supported by majority of controllers)
* Under config parameters settings, leave everything as it is.
* Make sure that the preemtion is enabled (preemtion based scheduling will be used which means a higher priority tasks can take control from lower one)
* 


<!-- 
* https://www.youtube.com/watch?v=muOL9SH0p9g&list=PLfIJKC1ud8gj1t2y36sabPT4YcKzmN_5D 
-->
