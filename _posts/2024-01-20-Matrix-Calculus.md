---
layout: post
title: Matrix Calculus
published: false
---

Linear algebra is important topic in control theory. Therefore I am going to make a post about matrix calculus.

The references below are very useful material for matrix calculus. The one and only Matrix Cookbook is found in [5], this is a document that includes a collection of facts about matrices and matters relating to them. An online vector and matrix calculator is found in [6] and useful material is found in [1], [2], [3] and [4]. This post is built on the references below and my own work.

# Notation

* **Scalars** are written as lower case letters. For example $$a,x,c,k,...$$.
* **Vectors** are written as lower case bold letters. For example $${\bf x}, {\bf b}, {\bf u}, ...$$. Vectors can be row vectors with dimensions $$1\times n$$ or column vectors with dimensions $$n \times 1$$. Column vectors are the default choice unless otherwise mentioned. Individual elements are indexed by subscripts, such as $$x_i \, \, (i \in \{1,\dots,n\})$$.
* **Matrices** are written as upper case bold letters. For example $${\bf A}, {\bf B}, {\bf X}, ...$$. Matrices have dimensions $$m \times n$$ with $$m$$ rows and $$n$$ columns. Individual elements are indexed by double subscripts for row and column, such as $$X_{ij} \, \, (i \in \{1, \dots ,m\}, \, j \in \{1,\dots,n\})$$.
* **Tensors** are of higher dimensions such as 3rd order tensor with dimension $$m \times n \times p$$, etc. Matrices are for example second order tensors. 

# Review of Matrix Derivatives

## 1st order derivative

### Linear Form

Let's consider the form $${\bf x}^T{\bf b}$$ where $${\bf x} \in \mathbb{R}^{n\times 1}$$ is a column vector of real numbers of dimension $$n \times 1$$ and $${\bf b}$$ is also a column vector of real numbers of dimension $$n \times 1$$. We can multiply these two vectors together by transposing $$\bf x$$ resulting in a linear combination.

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

this can be calculated as follows

$$\\
\begin{align}
\frac{\partial {\bf x}^T{\bf b}}{\partial {\bf x}} &= \begin{bmatrix} \frac{\partial {\bf x}^T{\bf b}}{\partial x_1} \\ \vdots \\ \frac{\partial {\bf x}^T{\bf b}}{\partial x_n} \end{bmatrix} \\
&= \begin{bmatrix} \frac{\partial}{\partial x_1} (b_1x_2 + \dots + b_nx_n) \\ \vdots \\ \frac{\partial}{\partial x_n} (b_1x_2 + \dots + b_nx_n) \end{bmatrix} \\
&= \begin{bmatrix} b_1 \\ \vdots \\ b_n \end{bmatrix} = {\bf b}
\end{align}
\\$$

### Quadratic Form

The quadratic matrix form is given by

$$\\
\begin{align}
{\bf x}^T{\bf A}{\bf x} &= \begin{bmatrix} x_1 & x_2 & x_3 & x_4 \end{bmatrix} \begin{bmatrix} a_{11} & a_{12} & a_{13} & a_{14} \\
a_{21} & a_{22} & a_{23} & a_{24} \\
a_{31} & a_{32} & a_{33} & a_{34} \\
a_{41} & a_{42} & a_{43} & a_{44} 
\end{bmatrix}
\begin{bmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \end{bmatrix} 
\end{align}
\\$$

Multiplying $${\bf x}^T{\bf A}$$ gives a pretty big row vector, we can define each index of that vector as

$$\\
\begin{align}
P_1 &= a_{11}x_1 + a_{21}x_2 + a_{31}x_3 + a_{41}x_4 \\
P_2 &= a_{12}x_1 + a_{22}x_2 + a_{32}x_3 + a_{42}x_4 \\
P_3 &= a_{13}x_1 + a_{23}x_2 + a_{33}x_3 + a_{43}x_4 \\
P_4 &= a_{14}x_1 + a_{24}x_2 + a_{34}x_3 + a_{44}x_4 
\end{align}
\\$$

Now we can define the quadratic form as

$$\\
\begin{align}
{\bf x}^T{\bf A}{\bf x} &= \begin{bmatrix} P_1 & P_2 & P_3 & P_4 \end{bmatrix} 
\begin{bmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \end{bmatrix} \\
&= P_1 x_1 + P_2 x_2 + P_3 x_3 + P_4 x_4.
\end{align}
\\$$

To not get too big equation I will introduce indexes again as

$$\\
\begin{align}
P_{11} &= x_1 (a_{11} x_1 + a_{21} x_2 + a_{31} x_3 + a_{41} x_4) \\
P_{22} &= x_2 (a_{12} x_1 + a_{22} x_2 + a_{32} x_3 + a_{42} x_4) \\
P_{33} &= x_3 (a_{13} x_1 + a_{23} x_2 + a_{33} x_3 + a_{43} x_4) \\
P_{44} &= x_4 (a_{14} x_1 + a_{24} x_2 + a_{34} x_3 + a_{44} x_4) 
\end{align}
\\$$

the quadratic form becomes

$$\\
\begin{align}
 {\bf x}^T{\bf A}{\bf x} &= \begin{bmatrix} P_{11} & P_{22} & P_{33} & P_{44} \end{bmatrix} \\
&=x_1 \sum_{i=1}^{n} a_{i1}x_i + x_2 \sum_{i=1}^{n} a_{i2}x_i + x_3 \sum_{i=1}^{n} a_{i3}x_i + x_4 \sum_{i=1}^{n} a_{i4}x_i 
\end{align}
\\$$

From this we can get the closed form solution

$$\\
\begin{align}
 {\bf x}^T{\bf A}{\bf x} &= x_1 \sum_{i=1}^{n} a_{i1}x_i + \dots + x_n \sum_{i=1}^{n} a_{in}x_i \\
 &= \sum_{j=1}^{n} x_j \sum_{i=1}^{n} a_{ij}x_i \\
 &= \sum_{j=1}^{n} \sum_{i=1}^{n} a_{ij}x_i x_j
\end{align}
\\$$

Let's find the derivative of the quadratic form. 

$$\\
\begin{align}
\frac{\partial {\bf x}^T{\bf A}{\bf x}}{\partial {\bf x}}  &= \begin{bmatrix} \frac{\partial {\bf x}^T{\bf A}{\bf x}}{\partial x_1} \\ \vdots \\ \frac{\partial {\bf x}^T{\bf A}{\bf x}}{\partial x_n} \end{bmatrix}
\end{align}
\\$$

Let's consider the $$k_{th}$$ row in the above vector

$$\\
\begin{align}
\frac{\partial {\bf x}^T{\bf A}{\bf x}}{\partial {\bf x}}  &= \frac{\partial}{\partial x_k} \left( \sum_{j=1}^{n} \sum_{i=1}^{n} a_{ij}x_i x_j \right) \\
&= \frac{\partial}{\partial x_k} \left( x_1 \sum_{i=1}^{n} a_{i1}x_i + \dots + x_k \sum_{i=1}^{n} a_{ik}x_i + \dots + x_n \sum_{i=1}^{n} a_{in}x_i \right) \\
&= x_1 a_{k1} + \dots + \left( \sum_{i=1}^{n} a_{ik}x_i + x_k a_{kk} \right) + \dots + x_n a_{kn} \\
&= \sum_{j=1}^{n} a_{kj}x_j + \sum_{i=1}^{n} a_{ik}x_i
\end{align}
\\$$


### ... This post is in progress.

#### References

[1] Review of simple matrix derivatives .H.K. Chen. SFU, Oct 2014. [Link to reference](https://www.sfu.ca/%7Ehaiyunc/notes/matrix_calculus.pdf)

[2] Matrix Calculus. Sourya Dey. [Link to reference](https://souryadey.github.io/teaching/material/Matrix_Calculus.pdf)

[3] Essential Concepts of Deep Learning. Sourya Dey. [Link to reference](https://www.overleaf.com/project/5afb2d49f2e25c77af32340f)

[4] Matrix Calculus. Wikipedia. [Link to reference](https://en.wikipedia.org/wiki/Matrix_calculus)

[5] The Matrix Cookbook. Kaare Petersen & Michael Petersen. 2012 [Link to reference](https://www.math.uwaterloo.ca/~hwolkowi/matrixcookbook.pdf)

[6] Online Vector and Matrix Calculator. [Link to reference](https://www.matrixcalculus.org/)
