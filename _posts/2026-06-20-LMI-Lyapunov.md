---
layout: post
title: "The Historical Origin of Linear Matrix Inequalities (LMIs)"
date: 2026-06-20
categories: control-theory optimization
published: true
---

# The Historical Origin of Linear Matrix Inequalities (LMIs)

Linear Matrix Inequalities (LMIs) are among the most powerful tools in modern control theory. They appear in applications ranging from stability analysis and robust control to Model Predictive Control (MPC) and optimal controller design.

Interestingly, the origins of LMIs can be traced back to the pioneering work of Russian mathematician Aleksandr Lyapunov in the late 19th century.

---

## The Stability Problem

Consider a linear time-invariant system

$$
\dot{x}(t) = Ax(t)
$$

where:

- $x(t)$ is the state vector
- $A$ is the system matrix

A fundamental question in control theory is:

> Will the state $x(t)$ converge to zero as time approaches infinity?

If the answer is yes, the system is said to be **asymptotically stable**.

---

## Lyapunov's Revolutionary Idea

Around 1890, Lyapunov introduced a method for determining stability without explicitly solving the differential equation.

Instead of finding the solution $x(t)$, he proposed searching for a scalar function that behaves like an "energy" measure of the system. For linear systems, a common choice is

$$
V(x) = x^T P x
$$

where $P$ is a symmetric matrix.

For $V(x)$ to represent energy, it must be positive for every nonzero state:

$$
P > 0
$$

meaning that $P$ is **positive definite**.

The next step is to examine how this energy changes over time.

---

## Where Does $A^T$ Come From?

Differentiating the Lyapunov function gives

$$
\dot{V}
=
\dot{x}^T P x
+
x^T P \dot{x}.
$$

Substituting the system dynamics

$$
\dot{x}=Ax
$$

yields

$$
\dot{V}
=
(Ax)^T P x
+
x^T P (Ax).
$$

Using the transpose identity

$$
(Ax)^T = x^T A^T,
$$

we obtain

$$
\dot{V}
=
x^T A^T P x
+
x^T P A x.
$$

Factoring out $x^T$ and $x$,

$$
\dot{V}
=
x^T(A^T P + PA)x.
$$

This is the famous Lyapunov matrix expression

$$
A^T P + PA.
$$

The transpose $A^T$ appears naturally during the differentiation of the quadratic function $V(x)=x^TPx$.

---

## The Lyapunov Stability Condition

If there exists a matrix $P$ such that

$$
P > 0
$$

and

$$
A^T P + PA < 0,
$$

then

$$
\dot{V} < 0
$$

for every nonzero state.

This means the system energy continuously decreases, forcing the state toward the origin.

Therefore, the system is asymptotically stable.

---

## Why Is This an LMI?

The inequality

$$
A^T P + PA < 0
$$

is called a **Linear Matrix Inequality (LMI)**.

To understand why, note that:

- $A$ is known.
- $P$ is unknown.
- Every entry of $A^T P + PA$ depends linearly on the entries of $P$.

There are no products between unknown variables and no nonlinear terms involving $P$.

Because the matrix expression is linear in the unknown matrix $P$, the condition is an LMI.

This is one of the earliest and most important LMIs in control theory.

---

## Solving the Lyapunov Inequality

Instead of solving

$$
A^T P + PA < 0
$$

directly, a common approach is to choose any positive definite matrix

$$
Q > 0
$$

and solve the Lyapunov equation

$$
A^T P + PA = -Q.
$$

Since $Q$ is known, this becomes a system of linear equations in the entries of $P$.

A popular choice is

$$
Q = I,
$$

which gives

$$
A^T P + PA = -I.
$$

If the resulting solution $P$ is positive definite, then the system is stable.

---

## Worked Example

Consider

$$
A=
\begin{bmatrix}
-1 & 0 \\
0 & -2
\end{bmatrix}
$$

and choose

$$
Q=I=
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}.
$$

Assume

$$
P=
\begin{bmatrix}
p_{11} & p_{12} \\
p_{12} & p_{22}
\end{bmatrix}.
$$

Substituting into

$$
A^T P + PA = -I
$$

gives

$$
\begin{bmatrix}
-2p_{11} & -3p_{12} \\
-3p_{12} & -4p_{22}
\end{bmatrix}
=
\begin{bmatrix}
-1 & 0 \\
0 & -1
\end{bmatrix}.
$$

Equating corresponding entries gives

$$
p_{11}=0.5,
$$

$$
p_{12}=0,
$$

$$
p_{22}=0.25.
$$

Therefore

$$
P=
\begin{bmatrix}
0.5 & 0 \\
0 & 0.25
\end{bmatrix}.
$$

Since both eigenvalues are positive, $P$ is positive definite.

Therefore, the system is asymptotically stable.

---

## Why LMIs Became So Important

Over the past few decades, researchers discovered that many control design problems can be expressed as LMIs.

Examples include:

- Stability analysis
- State-feedback control
- Observer design
- Robust control
- Gain scheduling
- Model Predictive Control (MPC)
- $H_\infty$ control

The key advantage is that LMIs define **convex optimization problems**.

Convex problems have a single global optimum and can be solved efficiently using modern semidefinite programming solvers.

This combination of strong mathematical guarantees and computational efficiency has made LMIs one of the foundational tools of modern control engineering.

---

## Final Thoughts

The simple condition

$$
A^T P + PA < 0
$$

may look like just another matrix inequality, but it represents one of the most influential ideas in control theory.

What began as Lyapunov's method for proving stability evolved into an entire framework for controller design and optimization.

Today, LMIs form the mathematical backbone of many advanced control techniques, connecting classical stability theory with modern convex optimization.

If you study modern control theory, optimization, MPC, robust control, or semidefinite programming, you will encounter LMIs repeatedly. Understanding the Lyapunov inequality is therefore one of the best starting points for learning the field.

---

#### References

[1] Linear Matrix Inequalities in System and Control Theory, Stephen Boyd, Laurent El Ghaoui, Eric Feron, and V. Balakrishnan. [Link](https://stanford.edu/~boyd/lmibook/lmibook.pdf)

[2] CVXGEN [Link](https://cvxgen.com/docs/index.html)
