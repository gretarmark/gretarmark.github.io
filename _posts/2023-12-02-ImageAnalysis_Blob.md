---
layout: post
title: Image Analysis - BLOB Analysis
published: true
---

BLOB Analysis (Binary Large OBject Analysis) is a method where pixels in an image are grouped together if they are connected. BLOB Analysis is also often called Connected Component Analysis or Object Labelling. 

Pixels are grouped together using 4- or 8-connectivity methods. These methods check the neighbours of each pixel in an image and check the connectivity between the neighbours and the pixel. If 4-connectivity is used, the algorithm checks four neighbours horizontally and vertically of each pixel as seen in figure [1]. On the other hand, if 8-connectivity as in figure [1] is used, the connectivity of all neighbours around each pixel is checked.

When connectivity of each pixel in the image beeing worked on have been analysed, we can say that all objects in the image have been grouped and can now have their own ID.  

![Fig 1]({{ site.baseurl }}/images/BlobAnalysis_4_8_Connected.png "zero order"){:width=75%}  
**Figure 1: 4- and 8- Connectivity Kernels.**

![Fig 2]({{ site.baseurl }}/images/BlobAnalysis_Image1.png "zero order"){:width=75%}  
**Figure 2: Binary Image.**


Robots interact with its environment using cameras, this is known as computer vision and is one of the most powerful sensing modalities that currently exist. In this post I will talk about 4- and 8- connectivity

* Median filter
* Average filter
* 
