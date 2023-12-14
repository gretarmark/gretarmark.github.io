---
layout: post
title: Linear Algebra - Review
published: true
---

Linear Algebra is fundamental in modern geometry and is probably the single most important topic in multiple areas of science. 
It is very common to approximate nonlinear equations by using Taylor expansion to get linear model of a system. 
When having a linear model of a system, you can apply linear algebra on it and it's much easier to solve than nonlinear algebra. 
I want this post to be a review of Linear Algebra including definitions and examples.

----

### Definition 1
Transpose of a matrix $$A$$ is given by $$A^T$$. A matrix $$A$$ with the property that $$A = A^T$$ is a symmetric matrix.

---

### Definition 2
A set of vectors $$V=\{v_1,v_2,...,v_l\}$$ each with the same dimension are said to be linearly independent if

$$
\alpha_1 v_1 + \alpha_2 v_2 + ... + \alpha_l v_l = 0 \qquad \text{implies that} \qquad \alpha_1 = \alpha_2 = ... = \alpha_l = 0,
$$

i.e., all scalars are 0. Otherwise, the set of vectors $$V$$ are said to be linearly dependent. 

---

### Definition 3
A square matrix $$A$$ is said to be invertible if there exists a square $$m \times m$$ matrix $$B$$ such that $$AB = I = BA$$ where $$I$$
is the $$m \times m$$ identity matrix. $$B$$ is called the inverse of $$A$$ and is denoted as $$B = A^{-1}$$. 
Matrix $$A$$ that has an inverse is said to be invertible of non-singular.

#### Theorem 3.1
A square $$m \times m$$ matrix $$A$$ is invertible if and only if the $$m$$ columns (rows) of $$A$$ form a linearly independent set of vectors.

It is worth mentioning that inverse of a square matrix $$A$$ plays an important role in the solution of linear systems of equations of the form

$$
Ax = b
$$

since the solution can be represented mathematically as $$x = A^{-1}b$$

---

### Definition 4

1. An $$n \times n$$ symmetric matrix $$A$$ is said to be positive semi-definite (PSD) if $$x^TAx \geq 0$$ for all vectors $$x$$ with dimension $$n$$. 
2. An $$n \times n$$ symmetric matrix $$A$$ is said to be positive definite (PD) if $$x^TAx > 0$$ for all vectors $$x$$ with dimension $$n$$ and $$x \neq 0$$.

---

#### Theorem 4.1

1. A positive definite matrix $$A$$ is invertible.
2. If the determinant of a matrix $$A$$ is non-zero, then $$A$$ is invertible.

Knowing whether a matrix is PSD or PD is useful in e.g. linear and quadratic programming, but it can be challenging to show that a matrix is PSD or PD. 

---

### Definition 5 - Determinant test for PD

Let $$A$$ be an $$m \times m$$ symmetric matrix. Let $$\Delta_l$$ be the determinant of the upper $$l \times l$$ submatrix of $$A$$ for $$1 \leq l \leq m$$.
$$\Delta_l$$ is called the lth principal minor of $$A$$. If $$\Delta_l > 0$$ for $$l = 1,...,m$$, then $$A$$ is positive definite.

#### Example 5.1

Let 

$$
A = \begin{bmatrix} 2 & -1 & -1 \\ -1 & 2 & 1 \\ -1 & 1 & 2 \end{bmatrix},
$$  

then $$\Delta_1 = \det(2) = 2 > 0$$, $$\Delta_2 = \det\left(\begin{bmatrix} 2 & -1 \\ -1 & 2 \end{bmatrix}\right) = 3 > 0$$, and $$\Delta_3 = \det\left(\begin{bmatrix} 2 & -1 & -1 \\ -1 & 2 & 1 \\ -1 & 1 & 2 \end{bmatrix}\right) = 2 > 0$$. Therefore $$A$$ is positive definite.

---

### Definition 6 - Eigenvalue test for PD

Another 

---
...in progress...

#### References

[1] Roy H. Kwon. Introduction to Linear Optimization and Extensions with Matlab-CRC press. 2013.
