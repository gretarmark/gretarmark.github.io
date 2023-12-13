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

**Definition 1** <br>
Transpose of a matrix $$A$$ is given by $$A^T$$. A matrix $$A$$ with the property that $$A = A^T$$ is a symmetric matrix.

---

**Definition 2** <br>
A set of vectors $$V=\{v_1,v_2,...,v_l\}$$ each with the same dimension are said to be linearly independent if

$$
\alpha_1 v_1 + \alpha_2 v_2 + ... + \alpha_l v_l = 0 \qquad \text{implies that} \qquad \alpha_1 = \alpha_2 = ... = \alpha_l = 0,
$$

i.e., all scalars are 0. Otherwise, the set of vectors $$V$$ are said to be linearly dependent. 

---

**Definition 3** <br>

#### References

[1] Roy H. Kwon. Introduction to Linear Optimization and Extensions with Matlab-CRC press. 2013.
