---
layout: post
title: Quadratic Programming
published: true
---

Convex Optimization is a topic in mathematics and engineering. It's about minimizing (or maximizing) a convex cost function. 
This can be done in a computer very quickly by using Quadratic Programming (QP).

Quadratic Programming (QP) is on the following form
$$
\text{minimize} \quad & \frac{1}{2}x^TPx + q^Tx + r \\
\text{such that (s.t.)} \quad & Gx \preceq h \\
& Ax = b
$$
