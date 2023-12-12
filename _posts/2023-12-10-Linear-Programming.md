---
layout: post
title: Linear Programming
published: true
---

I've always been really interested in making things work efficiently, especially in designing control systems. One thing I want to talk about is Linear Programming, which is a part of optimization theory. Optimization is used in controller techniques like LQR and MPC.

<br>

Linear Programming is about having a optimization objective function that is linear and all the constraint equalities and the constraint inequalities are also linear.

The formulation of a Linear Programming problem is on the form

$$\\

\begin{align}

\min_{\bf x} \quad & {\bf f}^T {\bf x} \tag{1.1}\\
\text{s.t.} \quad & {\bf Ax} \leq {\bf b} \tag{1.2}\\
& {\bf A}_{eq} {\bf x} = {\bf b}_{eq} \tag{1.3}\\
& {\bf l}_{b} \leq {\bf x} \leq {\bf u}_{b} \tag{1.4}

\end{align}

\\$$

where $$ {\bf f}^T $$ is a transposed vector of coefficients, $$\bf x$$ is a vector of the optimization variables, and these two form the objective function $${\bf f}^T {\bf x}$$. $$\min$$ stands for minimize and s.t. stands for "such that" (and "subject to").
The lower part under s.t. defines the equality and inequality constraints. $${\bf A}$$ is a matrix, $$\bf b$$ is a vector, $$ {\bf A}_{eq} $$ is a matrix, $${\bf b}_{eq}$$ is a vector, the lower and upper bounds $${\bf l}_b$$ and $${\bf u}_{b}$$ are vectors. 


Minimizing the objective function (also called cost function) is the same as maximizing the negative of it.

<br>
<br>

Let's take a look at an example where Matlab is used to solve a Linear Programming problem. 

We have the vectors 

$$
{\bf f} = \begin{bmatrix} 2 \\ -4 \\ 10 \end{bmatrix} \qquad \text{and} \qquad {\bf x} = \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix}
$$

The liner programming problem can be formulated as follows:

$$\\

\begin{align}

\min_{x_1,x_2,x_3} \quad & 2x_1 - 4x_2 + 10x_3 \\
\text{s.t.} \quad & 6x_1 + 3x_2 + 2x_3 \leq 140 \\
& 3x_1 - 3x_2 + 4x_3 \leq 60 \\
& x_1 + 3x_2 + 12x_3 = 20 \\
& 3x_1 + 2x_2 + 3x_3 = -10 \\
& -1200 \leq x_1 \leq 1200 \\
& -900 \leq x_2 \leq 900 \\
& -1300 \leq x_3 \leq 1300

\end{align}

\\$$

We want to minimize the objective function

$${\bf f}^T {\bf x} = \begin{bmatrix} 2 & -4 & 10 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} = 2x_1 - 4x_2 + 10x_3$$

such that

$$\begin{bmatrix} 6 & 3 & 2 \\ 3 & -3 & 4 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} \leq \begin{bmatrix} 140 \\ 60 \end{bmatrix} \\
\begin{bmatrix} -1200 \\ -900 \\ -1300 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} \leq \begin{bmatrix} 1200 \\ 900 \\ 1300 \end{bmatrix} \\
\begin{bmatrix} 1 & 3 & 12 \\ 3 & 2 & 3 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} \leq \begin{bmatrix} 20 \\ -10 \end{bmatrix}$$

which is the same as

$$
{\bf Ax} \leq {\bf b} \\
{\bf A}_{eq}{\bf x} \leq {\bf b}_{eq} \\
{\bf l}_b \leq {\bf x} \leq {\bf u}_b
$$

<!--
Test:
$$
\begin{align}
  \tag{1.1}
  V_{sphere} = \frac{4}{3}\pi r^3 = \underbrace{\begin{bmatrix} A & B \\ C & D \end{bmatrix}}_{A} \underbrace{\begin{bmatrix} A & B \\ C & D \end{bmatrix}}_{B}
\end{align}
$$

$$
\begin{align}
  \tag{1.1}
  V_{sphere} = \frac{4}{3}\pi r^3 = \underbrace{\begin{bmatrix} A & B \\ C & D \end{bmatrix}}_{A} \underbrace{\begin{bmatrix} A & B \\ C & D \end{bmatrix}}_{B}
\end{align}
$$
-->

Test:
<!--
$$
\begin{align}
  \underbrace{\begin{bmatrix} 6 & 3 & 2 \\ 3 & -3 & 4 \end{bmatrix}}_{\bf A} \underbrace{\begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix}}_{\bf x} \leq \underbrace{\begin{bmatrix} 140 \\ 60 \end{bmatrix}}_{\bf b}
\end{align}
$$

$$
\begin{align}
  \underbrace{\begin{bmatrix} -1200 \\ -900 \\ -1300 \end{bmatrix}}_{{\bf A}_{eq}} \underbrace{\begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix}}_{\bf x} \leq \underbrace{\begin{bmatrix} 1200 \\ 900 \\ 1300 \end{bmatrix}}_{{\bf b}_{eq}}
\end{align}
$$

$$
\begin{align}
  \underbrace{\begin{bmatrix} 1 & 3 & 12 \\ 3 & 2 & 3 \end{bmatrix}}\underline{\mathbf{l}\underline{b}} \cdot \underbrace{\begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix}}\underline{\mathbf{x}} \, \leq \, \underbrace{\begin{bmatrix} 20 \\ -10 \end{bmatrix}}\underline{\mathbf{u}\underline{b}}
\end{align}
$$
-->

<!--
$f(\protect\underline{p},t)$
-->

<!-- https://www.youtube.com/watch?v=WwMz2fJwUCg -->

#### References

[1] Linear Programming. Wikipedia. [Link to reference](https://en.wikipedia.org/wiki/Linear_programming)

[2] Matlab. Linear Programming. [Link to reference](https://se.mathworks.com/help/optim/ug/linprog.html)
