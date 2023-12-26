---
layout: post
title: Machine Learning - Neural Network
published: false
---

Neural Network (NN) with two hidden layers will be implemented from scratch in this post.

Two layer Neural Network (NN) means that we have one input layer where data is accepted into the NN, two hidden layers where the work is done, 
and an output layer where the data is sent out of the NN.

The dataset to be used is called the MNIST dataset [1]. The MNIST dataset is tens of thousands of these 28 by 28 low resolution grayscale images of handwritten digits.
Let's build a NN that classifies images of handwritten digits and tells you what digit is written in that image.

## The Math

We start by $$28 \times 28 = 784$$ pixel training images. Each of these pixels is just a pixel value between $$0$$ (black) and $$255$$ (white).
We have $$m$$ training images so we can represent it as matrix

$$
{\bf x} = \begin{bmatrix} \cdots x^{(1)} \cdots \\ \cdots x^{(2)} \cdots \\ \vdots \\ \cdots x^{(m)} \cdots \end{bmatrix}^T = \begin{bmatrix} \vdots & \vdots &  & \vdots \\ x^{(1)} & x^{(2)} & \cdots & x^{(m)} \\ \vdots & \vdots & & \vdots \end{bmatrix}
$$

Each row constitutes an example and each row is going to be 784 columns long because each of them is going to correspond to one pixel in that image. We need to transpose this matrix so each column will be an example instead of each row. The first column is therefore the first example (image) and will therefore have 784 rows corresponding to each pixel and we will have $$m$$ columns corresponding to $$m$$ training samples.

The goal is to take this image, do a bunch of processing and give out a prediction for what digit that image represents. We will do this with a Neural Network (NN).

* The first layer in the NN is going to be $$784$$ nodes, this is our input layer, each of the $$784$$ pixels maps to a node. 
* The second layer is going to be the hidden layer and it's going to have $$10 units$$.
* The third layer is going to be the output layer with 10 units and each corresponding to one digit that can be predicted

The first layer is actually the 0th layer, second layer is actually the 1st layer and so on. The 1st layer (2nd) is the first hidden layer, the input is not really a layer.

There are three parts to training this network
* Forward Propagation
* ?
* ?

### Forward Propagation

Forward propagation is when you take an image and you run it through the NN, in that process you compute what the output from the NN is going to be.
So that's the first part we need to figure out.
First we have the input layer $${\bf A}^{\[0\]}$$ given by

$$
{\bf A}^{\[0\]} = {\bf x}
$$

The first layer is simple, just equal to $${\bf x}$$, there is no processing going on.

Next we have $${\bf Z}^{\[1\]}$$, which is the unactivated first layer (hidden layer) given by

$$
{\bf Z}^{\[1\]} = {\bf W}^{\[1\]} {\bf A}^{\[0\]} + {\bf b}^{\[1\]} 
$$

where $${\bf Z}^{\[1\]} \in \mathbf{R}^{10 \times m}$$, $${\bf W}^{\[1\]} \in \mathbf{R}^{10 \times 784}$$, $${\bf A}^{\[0\]} \in \mathbf{R}^{784 \times m}$$, and $${\bf b}^{\[1\]} \in \mathbf{R}^{10 \times 1}$$. To get $${\bf Z}^{\[1\]}$$ we apply weight and a bias, we take the dot product of $$\bf W$$ and $$\bf A$$ and that is going to give us something, and it's good to add the bias term $$\bf b$$ to it.

In the NN we multiply a bunch of weights that correspond to each of the connections in it, it's like $$10\cdot 784 = 7840$$ connections, then we add a constant bias term to each of the nodes. 










#### References

[1] Wikiwand. [Link to reference](https://www.wikiwand.com/en/MNIST_database)

[2] YouTube. Samson Zhang. [Link to reference](https://www.youtube.com/watch?v=w8yWXqWQYmU)
