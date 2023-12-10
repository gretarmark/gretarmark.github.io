---
layout: post
title: Linear Programming
published: true
---

I've always been really interested in making things work efficiently, especially in designing control systems. One thing I want to talk about is Linear Programming, which is a part of optimization theory. In this post, I'll break down what Linear Programming is all about and show you why it's so important for creating smart and efficient control systems.

Linear Programming is about having a optimization objective function that is linear and all the constraint equalities/inequalities are also linear.

The formulation of a Linear Programming problem is on the form

$$\\

\begin{align}

\min_{x} \quad & {\bf f}^T {\bf x} \\
\text{s.t.} \quad & {\bf Ax} \leq {\bf b} \\
& {\bf A}_{eq} {\bf x} = {\bf b}_{eq} \\
& {\bf l}_{b} \leq {\bf x} \leq {\bf u}_{b}

\end{align}

\\$$

where 

$$\\

\begin{mini}|l|
	  {w,u}{f(w)+ R(w+6x)}{}{}
	  \addConstraint{g(w_k)+h(w_k)}{=0,}{k=0,\ldots,N-1}
	  \addConstraint{l(w_k)}{=5u,\quad}{k=0,\ldots,N-1}
\end{mini}

\\$$

<!-- https://www.youtube.com/watch?v=bOKbSSxo8TA -->

#### References

[1]  B
