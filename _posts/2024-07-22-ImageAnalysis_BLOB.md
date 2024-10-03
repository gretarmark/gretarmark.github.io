---
layout: post
title: BLOB Analysis in Image Processing
published: true
---

BLOB Analysis, which stands for "Binary Large Object Analysis", is a crucial topic in image processing and computer vision. 
It involves the grouping of pixels in an image based on connectivity and shared properties, such as intensity or color.
A key component of BLOB extraction is Connected Component Analysis (CCA) [1], which refers to the process of identifying and labeling connected components
in a binary image.
In this post, I will discuss CCA and how to extract objects from an image.

In Connected Component Analysis, pixels are grouped together using either 4-connectivity or 8-connectivity methods.
This methodology checks the connectivity of each pixel to its neighbors. The two connectivity kernels are illustrated in Figure 1.
In 4-connectivity, the algorithm checks two horizontal and two vertical neighbors for each pixel. 
Conversely, 8-connectivity examines all neighboring pixels surrounding each pixel.

![Fig 1]({{ site.baseurl }}/images/BlobAnalysis_4_8_Connected.png "zero order"){:width="50%"}  
**Figure 1: BLOB 4- and 8-Connectivity Kernels.**

![Fig 2]({{ site.baseurl }}/images/BlobAnalysis_Image1.png "zero order"){:width="40%"}  
**Figure 2: Binary Image. In this image, blue represents a value of 1, and white represents a value of 0.
The coordinate system is anchored to the upper left corner. 
In Matlab, the first pixel is at (1,1), while in a camera system programmed in C, it is at (0,0).**

The binary image shown in Figure 2 can be implemented in Matlab using the following matrix code snippet: 

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

The "imagesc" function displays the data matrix as an image, utilizing the full range of colors in the colormap. 
The image forms an $$m \times n = 10 \times 9$$ grid of pixels, where $$m$$ is the number of rows and $$n$$ is the number of columns. 
The resulting image is shown in Figure 3.

![Fig 3]({{ site.baseurl }}/images/BlobAnalysis_Matlab1.png "zero order"){:width="60%"}  
**Figure 3: The image after using the Matlab function "imagesc()".**

Next, we will apply the 4- and 8-connectivity kernels to the image using the Matlab function "bwlabel()". With 4-connectivity, the algorithm detects 5 objects in the image, while applying the 8-connectivity kernel results in the detection of 4 objects, as illustrated in Figure 4.

![Fig 4]({{ site.baseurl }}/images/BlobAnalysis_Matlab2.png "zero order"){:width="90%"}  
**Figure 4: Results of 4- and 8- connectivity applied to the image.**

To enhance visualization, we can use the MATLAB function "label2rgb()" to generate the image shown in Figure 5.

![Fig 5]({{ site.baseurl }}/images/BlobAnalysis_Matlab3.png "zero order"){:width="100%"}  
**Figure 5: Output after applying "label2rgb()".**

Additionally, we can calculate the area of each object using the MATLAB function "regionprops()". The areas of the detected objects are as follows:

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

<!--The algorithm used to do BLOB analysis is called "The Grass-Fire Algorithm". It starts in the upper-left corner of the binary image and then scans the entire image from left to right and from top to bottom.
At some point during the scan, an object pixel (white pixel) is encountered. At this point you can imagine yourself standing in a field covered with dry grass. -->

The algorithm used for BLOB analysis is called "The Grass-Fire Algorithm". It begins in the upper-left corner of the binary image, scanning from left to right and top to bottom. When an object pixel is encountered, imagine standing on that pixel in a field covered with dry grass, with four arms, each holding a burning match. As you stretch out your arms and drop the matches, a fire spreads in four different directions (right, down, left, up), burning all connected straws. This metaphor illustrates how the algorithm identifies connected components.

In the binary image, the pixels representing objects are akin to the dry grass, while non-object pixels represent water. Using 4-connectivity, the algorithm looks in four directions for object pixels. When it finds one, it performs two actions:

1. It labels the pixel in the output image with an object ID.
2. It "burns" that pixel in the input image by setting it to zero, indicating it has been processed and will not be counted again.

![Fig 6]({{ site.baseurl }}/images/BlobAnalysis_Matlab4.png "zero order"){:width="40%"}  
**Figure 6: Application of the 4-connectivity Grass-Fire Algorithm on the binary image.**

The algorithm continues scanning the image in this manner.

BLOB analysis serves as a foundation advanced methods in feature detection, 
playing a crucial role in artificial intelligence systems for recognizing objects such as humans, fruits, animals, license plates, and more.
Further exploration in this field may include topics such as:

* BLOB Bounding Box
* Bounding Box Ratio
* Bounding Circle
* Convex Hull
* Compactness
* Center of Mass for Image Analysis
* Perimeter
* Circularity
* BLOB Classification
* Training Data through Feature Learning
* Feature Selection and Ranges
* Evaluation of Classification
* Object Labelling
* Object Recognition
* Image Segmentation


#### References
[1] "Connected Component Labeling." Wikipedia. Visited 2. Dec 2023: [Link to reference](https://en.wikipedia.org/wiki/Connected-component_labeling)



