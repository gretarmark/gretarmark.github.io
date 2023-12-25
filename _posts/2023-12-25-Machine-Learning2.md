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
{\bf x} = \begin{bmatrix} ... x^{(1)}... \\ ... x^{(2)}... \\ ... \\ ... x^{(m)}... \end{bmatrix}^T = \begin{bmatrix} ... & ... &  & ... \\ x^{(1)} & x^{(2)} & ... & x^{(m)} \\ ... & ... & & ... \end{bmatrix}
$$


#### References

[1] Wikiwand. [Link to reference](https://www.wikiwand.com/en/MNIST_database)