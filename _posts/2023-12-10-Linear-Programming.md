---
layout: post
title: Linear Programming
published: true
---

I've always been really interested in making things work efficiently, especially in designing control systems. One thing I want to talk about is Linear Programming, which is a part of optimization theory. In this post, I'll break down what Linear Programming is all about and show you why it's so important for creating smart and efficient control systems.

Linear Programming is about having a optimization objective function that is linear and all the constraint equalities and the constraint inequalities are also linear.

The formulation of a Linear Programming problem is on the form

$$\\

\begin{align}

\min_{x} \quad & {\bf f}^T {\bf x} \\
\text{s.t.} \quad & {\bf Ax} \leq {\bf b} \\
& {\bf A}_{eq} {\bf x} = {\bf b}_{eq} \\
& {\bf l}_{b} \leq {\bf x} \leq {\bf u}_{b}

\end{align}

\\$$

where $$ {\bf f}^T $$ is a transposed vector of coefficients, $$\bf x$$ is a vector of the optimization variables, and these two form the objective function {\bf f}^T {\bf x}. $$\min$$ stands for minimize and s.t. stands for "such that".
The lower part under s.t. defines the equality and inequality constraints. $${\bf A}$$ is a matrix, $$\bf b$$ is a vector, $$ {\bf A}_{eq} $$ is a matrix, $${\bf b}_{eq}$$ is a vector, the lower and upper bounds $${\bf l}_b$$ and $${\bf u}_{b}$$ are vectors. 


Minimizing the objective function (also called cost function) is the same as maximizing the negative of it.

Let's take a look at an example. Let's choose

$$ {\bf f}^T = \begin{bmatrix} 2 & 4 & 10 \end{bmatrix}$$ 

so the objective function becomes

$${\bf f}^T {\bf x} = \begin{bmatrix} 2 & 4 & 10 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} = 2x_1 + 4x_2 + 10x_3$$

 


<!-- https://www.youtube.com/watch?v=bOKbSSxo8TA -->

#### References

[1]  B
