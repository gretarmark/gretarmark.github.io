---
layout: post
title: Image Analysis - BLOB Analysis
published: true
---

BLOB Analysis (Binary Large OBject Analysis) is a method where pixels in an image are grouped together if they are connected. BLOB Analysis is also often called Connected Component Analysis or Object Labelling. 

Pixels are grouped together using 4- or 8-connectivity methods. This methology involves checking the connectivity from a pixel to its neighbours. The two kernels are shown in figure [1]. If 4-connectivity is used, the algorithm checks two neighbours horizontally and two neighbours vertically of each pixel. On the other hand, if 8-connectivity is used, the connectivity of all neighbours around each pixel is checked. 

![Fig 1]({{ site.baseurl }}/images/BlobAnalysis_4_8_Connected.png "zero order"){:width="50%"}  
**Figure 1: BLOB 4- and 8-Connectivity Kernels.**

![Fig 2]({{ site.baseurl }}/images/BlobAnalysis_Image1.png "zero order"){:width="40%"}  
**Figure 2: Binary Image. Blue represents 1 and white represents 0. The coordinate system is attached to the upper left corner. In Matlab, the first pixel is at (1,1), but in a camera system the first pixel is at (0,0).**

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

To visualize the image more effectively, it's advisable to use the Matlab function label2rgb() to obtain the image shown in figure [5].

![Fig 5]({{ site.baseurl }}/images/BlobAnalysis_Matlab3.png "zero order"){:width="100%"}  
**Figure 5: label2rgb() applied to the image.**

It is possible to count the area of each object using the Matlab function regionprops(). The area of each object is as follows:

4-Connectivity (5 objects):
* Area of object 1: 5 pixels
* Area of object 2: 10 pixels
* Area of object 3: 1 pixels
* Area of object 4: 5 pixels
* Area of object 5: 8 pixels

8-Connectivity (4 objects):
* Area of object 1: 5 pixels
* Area of object 2: 10 pixels
* Area of object 3: 1 pixels
* Area of object 4: 13 pixels

"The algorithm used to do BLOB analysis is called "The Grass-Fire Algorithm". It starts in the upper-left corner of the binary image and then scans the entire image from left to right and from top to bottom.
At some point during the scan, an object pixel (white pixel) is encountered. At this point you can imagine yourself standing in a field covered with dry grass. Imagine you have four arms"

The algorithm used to do BLOB analysis is called "The Grass-Fire Algorithm". It starts in the upper-left corner of the binary image and then scans the entire image from left to right and from top to bottom. When an object pixel is encountered, you can imagine that you are standing in that pixel and all around you is a field covered with a dry grass. Let's say you have four arms and in each of them you are holding a burning match. You then stretch out your arms and drops the burning matches. When they are dropped, they will start a fire which will spread in four different directions (right, down, left, up). This will result in a great fire where each single straw that is connected to your initial position will burn. This is the explanation of the algorithm.

In the binary image, the pixels of the objects are the dry grass I talked about, and the non-object pixels are water. If we use 4-connectivity, the algorithm looks into four different directions. If it finds a pixel which can be burned (object pixel), it does two things:

1. In the output image, it will give that pixel an object label (some ID).
2. It will burn that pixel in the input image and set it to zero. Setting it to zero indicates it has been burned and therefore it will not be part of another fire.

![Fig 6]({{ site.baseurl }}/images/BlobAnalysis_Matlab4.png "zero order"){:width="100%"}  
**Figure 6: The 4-connectivity Grass-Fire Algorithm applied to the binary image above.**

In computers, the algorithm is performed as follows:
* The first object pixel is labeld 1, let's say it's at (1,7) as in the binary image in figure [6]. This pixel has to be marked so the computer knows it has been burned, it is marked by 1 in the lower right corner. 
* Next, the algorithm tries to start a fire at the first neighbour (1,8), it checks if it is an object pixel, since it's not, the pixel (1,8) is not marked as a burned pixel, it's just a water.
* The algorithm next checks pixel (2,7), since it is an object pixel it will "burn" the pixel and mark it as burned by adding 1 to the lower right corner.
* Each time the algorithm "burns" an pixel, it will move the center of the 4-connectivity kernel to that pixel, therefore the next pixel to check is the neighbour at pixel (2,8).
* Since (2,8) is an object pixel, the center of the 4-connectivity kernel is moved to that pixel, and pixel (2,8) is marked with 1 in the lower right corner. 
* Next it checks pixel (2,9) and figures out it is a water. Then it checks pixel (3,8) and it burns that pixel by marking it with 1 in the lower right corner.
* This is how the algorithm works and it scans like this through the whole image.

<!--When connectivity of each pixel in the image beeing worked on have been analysed, we can say that all objects in the image have been grouped and can now be given their own ID.   

Robots interact with its environment using cameras, this is known as computer vision and is one of the most powerful sensing modalities that currently exist. In this post I will talk about 4- and 8- connectivity

* Median filter
* Average filter
* 


#### References
[1] imagesc [Link to reference](https://se.mathworks.com/help/matlab/ref/imagesc.html)

[2] bwlabel() [Link to reference](https://se.mathworks.com/help/images/ref/bwlabel.html)

[3] label2rgb() [Link to reference](https://se.mathworks.com/help/images/ref/label2rgb.html)

[4] regionprops() [Link to reference](https://se.mathworks.com/help/images/ref/label2rgb.html)

-->
