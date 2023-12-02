---
layout: post
title: Image Analysis - BLOB Analysis
published: true
---

BLOB Analysis (Binary Large Object Analysis) is a method where pixels in an image are grouped together if they are connected.

Blob Analysis is also often called Connected Component Analysis or Object Labelling. 

Pixels are grouped together using 4- or 8 connectivity methods. After objects have been grouped, they will have their own ID in the image.  

![Fig 1]({{ site.baseurl }}/images/BlobAnalysis_4_8_Connected.png "zero order"){:width=75%}  
**Figure 1: 4- and 8- Connectivity Kernels.**


Robots interact with its environment using cameras, this is known as computer vision and is one of the most powerful sensing modalities that currently exist. In this post I will talk about 4- and 8- connectivity

* Median filter
* Average filter
* 
