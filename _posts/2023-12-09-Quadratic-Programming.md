---
layout: post
title: Quadratic Programming
published: false
---

Convex Optimization is a topic in mathematics and engineering. It's about minimizing (or maximizing) a convex objective function (also called cost function). 
This can be done in a computer very quickly by using Quadratic Programming (QP).

Quadratic Programming (QP) problem is on the following form

$$\\

\begin{align}

\text{minimize} \quad & \frac{1}{2}x^TPx + q^Tx + r \\
\text{s.t.} \quad & Gx \preceq h \\
& Ax = b

\end{align}

\\$$

* $$P \in {\bf S}_+^{n}$$, so objective is convex quadratic.
* Minimize a convex quadratic function over a polyhedron.

In general, not always, if $$P$$ is not positive semi-definite, so if it got literally one negative eigenvalue or something like that, solving this problem goes from being extremely straight forward to NP-hard [1]. This means it goes from a problem that is in theory would assert that this problem is now very hard to solve and also in practice, where you go from a problem where you can solve the exact solution{}

If $$P$$ becomes indefinite these problems becomes almost impossible to solve. So, convexity makes all the difference with quadratic programs. 

Quadratic Programming (QP) problem with constraints can be for example

$$\\

\begin{align}

\text{minimize} \quad & \frac{1}{2}x^TP_0x + q_0^Tx + r_0 \\
\text{s.t.} \quad & \frac{1}{2}x^TP_ix + q_i^Tx + r_i, \quad i=1,...,m \\
& Ax = b

\end{align}

\\$$

* $$P_i \in {\bf S}_+^{n}$$; objective and constraints are convex quadratic.
* Minimize a convex quadratic function over a polyhedron.


#### References

[1] NP-hardness. Wikipedia. [Link to reference](https://en.wikipedia.org/wiki/NP-hardness)

[2] Convex Optimization Lecture 6. Stanford. Stephen Boyd. [Link to reference](https://www.youtube.com/watch?v=-T9cloGG_80&t=631s) 





