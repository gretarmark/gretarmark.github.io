---
layout: post
title: Including C++ Libraries in Visual Studio
published: false
---

In this post I will explain how to include external library from C++ in Visual Studio IDE.

There are two types of linking; **Static liniking** and **dynamic linking**.

The very first think to do when including library is to include the headers. To include the headers, go to the **"solution expolorer"** of the project and right click on the project name and choose **"properties"**. Under **"Configuration Properties->C/C++"**, on the very top, is a settings called **"Additional Include Directories"**, you put the path to the folder that includes all the headers of the library in this place. After doing that, the program recognize the library, but there is more to do. It is important that the library you import matches the project regarding 32bit or 64 bit, make sure it does.

Static linking is when you build your project and all of the files from the library will be included in the project, in one application. On the other hand, dynamic linking is when all of the files from the library is not included in one application in the project, the actual files of the library will be in the same directory as the application, so during runtime, the application will use the library files.

Dynamic linking can be slower in runtime since the compiler needs to find the files of the library.

Most often there are three files from libraries that needs to be included:
* Two .dll files
* One .lib file

To link staticly, you need to inclue the libraries. You want to choose the **".lib"** file and You go now to the **"linker->general"** and there is a settings called **"additional library directories"**, you need to add the path to the library in that settings.

To link dynamically, you need to include a "...dll.dll" file in the "input->additional dependencies"


<!-- https://www.youtube.com/watch?v=ZYLKI8FxiD8 -->
