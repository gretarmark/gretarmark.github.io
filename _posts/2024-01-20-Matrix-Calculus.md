---
layout: post
title: Matrix Calculus
published: true
---

Linear algebra is important topic in control theory. Therefore I am going to make a post about matrix calculus.

The references below are very useful material for matrix calculus. The one and only Matrix Cookbook is found in [5], this is a document that includes a collection of facts about matrices and matters relating to them. An online vector and matrix calculator is found in [6]. And useful material is found in [1], [2], [3] and [4]. This post is built on the references below and my own work.

## Notation

* **Scalars** are written as lower case letters. For example $$a,x,c,k,...$$.
* **Vectors** are written as lower case bold letters. For example $${\bf x}, {\bf b}, {\bf u}, ...$$. Vectors can be row vectors with dimensions $$1\times n$$ or column vectors with dimensions $$n \times 1$$. Column vectors are the default choice unless otherwise mentioned. Individual elements are indexed by subscripts, such as $$x_i \, \, (i \in \{1,\dots,n\})$$.
* **Matrices** are written as upper case bold letters. For example $${\bf A}, {\bf B}, {\bf X}, ...$$. Matrices have dimensions $$m \times n$$ with $$m$$ rows and $$n$$ columns. Individual elements are indexed by double subscripts for row and column, such as $$X_{ij} \, \, (i \in \{1, \dots ,m\}, \, j \in \{1,\dots,n\})$$.
* **Tensors** are of higher dimensions such as 3rd order tensor with dimension $$m \times n \times p$$, etc. Matrices are for example second order tensors. 

## Review of Matrix Derivatives

Let's consider the form $${\bf x}^T{\bf b}$$ where $${\bf x} \in \mathbf{R}^{n\times 1}$$ is a column vector of real numbers of dimension $$n \times 1$$ and $${\bf b}$$ is also a column vector of real numbers of dimension $$n \times 1$$. We can multiply these two vectors together by transposing $$\bf x$$ resulting in a linear combination.

$$\\

\begin{align}

{\bf x}^T {\bf b} = \begin{bmatrix} x_1 & \dots & x_n \end{bmatrix} \begin{bmatrix} b_1 \\ \vdots \\ x_n \end{bmatrix} = b_1x_2 + \dots + b_n x_n

\end{align}

\\$$

According to [5], page 10, chapter 2.4.1, the derivative of $${\bf x}^T{\bf b}$$ is 

$$\\

\begin{align}

\frac{\partial {\bf x}^T{\bf b}}{\partial {\bf x}} = \frac{\partial {\bf b}^T{\bf x}}{\partial {\bf x}} = {\bf b}

\end{align}

\\$$




#### References

[1] Review of simple matrix derivatives .H.K. Chen. SFU, Oct 2014. [Link to reference](https://www.sfu.ca/%7Ehaiyunc/notes/matrix_calculus.pdf)

[2] Matrix Calculus. Sourya Dey. [Link to reference](https://souryadey.github.io/teaching/material/Matrix_Calculus.pdf)

[3] Essential Concepts of Deep Learning. Sourya Dey. [Link to reference](https://www.overleaf.com/project/5afb2d49f2e25c77af32340f)

[4] Matrix Calculus. Wikipedia. [Link to reference](https://en.wikipedia.org/wiki/Matrix_calculus)

[5] The Matrix Cookbook. Kaare Petersen & Michael Petersen. 2012 [Link to reference](https://www.math.uwaterloo.ca/~hwolkowi/matrixcookbook.pdf)

[6] Online Vector and Matrix Calculator. [Link to reference](https://www.matrixcalculus.org/)
