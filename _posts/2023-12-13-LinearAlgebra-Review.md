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

A square $$m \times m$$ matrix $$A$$ is invertible if and only if the $$m$$ columns (rows) of $$A$$ form a linearly independent set of vectors.

#### Example

It is worth mentioning that inverse of a square matrix $$A$$ plays an important role in the solution of linear systems of equations of the form

$$
Ax = b
$$

since the solution can be represented mathematically as $$x = A^{-1}b$$

---

### Definition 4

#### References

[1] Roy H. Kwon. Introduction to Linear Optimization and Extensions with Matlab-CRC press. 2013.
