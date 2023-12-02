---
layout: post
title: Image Analysis - BLOB Analysis
published: true
---

BLOB Analysis (Binary Large OBject Analysis) is a method where pixels in an image are grouped together if they are connected. BLOB Analysis is also often called Connected Component Analysis or Object Labelling. 

Pixels are grouped together using 4- or 8-connectivity methods. This methology is about checking the connectivity from a pixel to its neighbours. The two kernels are shown in figure [1]. If 4-connectivity is used, the algorithm checks two neighbours horizontally and two neighbours vertically of each pixel. On the other hand, if 8-connectivity is used, the connectivity of all neighbours around each pixel is checked. If a pixel have 4/8 or more neighbours, the connectivity check is fulfilled.

![Fig 1]({{ site.baseurl }}/images/BlobAnalysis_4_8_Connected.png "zero order"){:width="50%"}  
**Figure 1: BLOB 4- and 8-Connectivity Kernels.**

![Fig 2]({{ site.baseurl }}/images/BlobAnalysis_Image1.png "zero order"){:width="40%"}  
**Figure 2: Binary Image. Blue represents 1 and white represents 0. The coordinate system is attached to the upper left corner.**

The image in figure [2] can be implemented in Matlab by using the following matrix code snip: 

```Matlab
img = [0 0 0 0 0 0 1 0 0
       0 0 0 1 0 1 1 1 0
       0 1 0 0 0 0 1 1 0
       1 1 1 0 0 0 0 1 1
       0 1 0 0 0 1 1 0 0
       0 0 0 0 1 1 1 0 0
       0 0 0 0 0 0 0 0 0
       0 1 1 1 0 0 0 0 0
       0 1 1 1 1 0 0 0 0
       0 1 1 1 0 0 0 0 0];

imagesc(img);
size(img)
```

The function "imagesc" displays the data matrix as an image that uses the full range of colors in the colormap. The image is an $$m \times n = 10 \times 9$$ grid of pixels where $$m$$ is number of rows and $$n$$ is number of columns. The new image is shown in figure 3.

![Fig 3]({{ site.baseurl }}/images/BlobAnalysis_Matlab1.png "zero order"){:width="60%"}  
**Figure 3: The image after using the Matlab function "imagesc()".**

Let's now apply 4- and 8-connectivity kernels on the image using the Matlab function bwlabel(). It can be seen that using 4-connectivity, the algorithm detects 5 objects in the image. On the other hand, by applying the 8-connectivity kernel on the image, the algorithm detects 4 objects in the image as shown in figure 4.

![Fig 4]({{ site.baseurl }}/images/BlobAnalysis_Matlab2.png "zero order"){:width="90%"}  
**Figure 4: 4- and 8- connectivity applied to the image.**

To visualize the image in a better way, it's good to use the Matlab function label2rgb() to obtain the image in figure [5]

![Fig 5]({{ site.baseurl }}/images/BlobAnalysis_Matlab3.png "zero order"){:width="100%"}  
**Figure 5: label2rgb() applied to the image.**

It is possible to count the objects using the 

<!--When connectivity of each pixel in the image beeing worked on have been analysed, we can say that all objects in the image have been grouped and can now be given their own ID.   

Robots interact with its environment using cameras, this is known as computer vision and is one of the most powerful sensing modalities that currently exist. In this post I will talk about 4- and 8- connectivity

* Median filter
* Average filter
* 
-->

#### References
[1] imagesc [Link to reference](https://se.mathworks.com/help/matlab/ref/imagesc.html)

[2] bwlabel() [Link to reference](https://se.mathworks.com/help/images/ref/bwlabel.html)

[3] label2rgb() [Link to reference](https://se.mathworks.com/help/images/ref/label2rgb.html)
