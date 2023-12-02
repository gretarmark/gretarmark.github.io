---
layout: post
title: Image Analysis - BLOB Analysis
published: true
---

BLOB Analysis (Binary Large OBject Analysis) is a method where pixels in an image are grouped together if they are connected. BLOB Analysis is also often called Connected Component Analysis or Object Labelling. 

Pixels are grouped together using 4- or 8-connectivity methods. This methology is about checking the connectivity from a pixel to each of its neighbour. The two kernels are shown in figure [1]. If 4-connectivity is used, the algorithm checks two neighbours horizontally and two neighbours vertically of each pixel. On the other hand, if 8-connectivity is used, the connectivity of all neighbours around each pixel is checked. If a pixel have 4/8 or more neighbours, the connectivity check is fulfilled.

When connectivity of each pixel in the image beeing worked on have been analysed, we can say that all objects in the image have been grouped and can now have their own ID.  

![Fig 1]({{ site.baseurl }}/images/BlobAnalysis_4_8_Connected.png "zero order"){:width=50%}  
**Figure 1: 4- and 8- Connectivity Kernels.**

![Fig 2]({{ site.baseurl }}/images/BlobAnalysis_Image1.png "zero order"){:width=40%}  
**Figure 2: Binary Image.**


Robots interact with its environment using cameras, this is known as computer vision and is one of the most powerful sensing modalities that currently exist. In this post I will talk about 4- and 8- connectivity

* Median filter
* Average filter
* 
