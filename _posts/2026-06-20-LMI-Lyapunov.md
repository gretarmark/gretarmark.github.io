---

layout: post
title: "The Historical Origin of Linear Matrix Inequalities (LMIs)"
date: 2026-06-20
categories: control-theory optimization
published: true
---

Imagine you are designing the control system for a drone, an autonomous vehicle, a robot, or a power plant.

Before deploying the controller, you need to answer a fundamental question:

> Will the system remain stable?

For simple systems, it is sometimes possible to solve the differential equations and directly examine the solution. However, for realistic engineering systems this quickly becomes impractical.

More than 130 years ago, Russian mathematician Aleksandr Lyapunov developed a remarkable alternative. Instead of solving the differential equations, he proposed studying an energy-like function whose value decreases over time.

This idea eventually led to one of the most important tools in modern control theory: **Linear Matrix Inequalities (LMIs)**.

Today, LMIs are used in stability analysis, robust control, observer design, Model Predictive Control (MPC), and many other advanced control techniques.

---

## A Brief Historical Perspective

In 1892, Lyapunov published his doctoral dissertation *The General Problem of Stability of Motion*.

At the time, stability analysis was largely based on finding explicit solutions to differential equations. Lyapunov introduced a completely different viewpoint: determine stability without solving the system itself.

His approach was so powerful that it became one of the foundations of modern control theory.

Although the term *Linear Matrix Inequality* would not appear until many decades later, the famous Lyapunov condition

$$
A^T P + PA < 0
$$

is now recognized as one of the earliest and most important examples of an LMI.

---

## The Stability Problem

Consider the linear time-invariant system

$$
\dot{x}(t)=Ax(t)
$$

where:

* $$x(t)$$ is the state vector
* $$A$$ is the system matrix

The fundamental question is:

> Will the state $$x(t)$$ converge to zero as time approaches infinity?

If the answer is yes, the system is said to be **asymptotically stable**.

---

## Lyapunov's Revolutionary Idea

Instead of solving the differential equation directly, Lyapunov proposed searching for a scalar function that behaves like an energy measure of the system.

For linear systems, a common choice is

$$
V(x)=x^TPx
$$

where $$P$$ is a symmetric matrix.

You can think of $$V(x)$$ as a generalized energy function.

For mechanical systems, energy consists of kinetic and potential energy. For a general linear system, the quadratic form $$x^TPx$$ plays a similar role.

For $$V(x)$$ to represent energy, it must be positive for every nonzero state:

$$
P>0.
$$

This means that $$P$$ is **positive definite**.

The next step is to determine whether this energy increases or decreases over time.

---

## Deriving the Lyapunov Stability Condition

To determine how the energy changes, we compute the time derivative of $$V(x)$$:

$$
\dot{V} = \dot{x}^TPx + x^TP\dot{x}.
$$

Substituting the system dynamics

$$
\dot{x}=Ax
$$

gives

$$
\dot{V} = (Ax)^TPx + x^TP(Ax).
$$

Using the transpose identity

$$
(Ax)^T=x^TA^T,
$$

we obtain

$$
\dot{V} = x^TA^TPx + x^TPAx.
$$

Factoring out $$x^T$$ and $$x$$,

$$
\dot{V} = x^T(A^TP+PA)x.
$$

This expression determines whether the system's energy increases or decreases over time.

If the matrix

$$
A^TP+PA
$$

is negative definite, then

$$
\dot{V}<0
$$

for every nonzero state.

In other words, the energy continuously decreases, forcing the state toward the equilibrium point.

This leads directly to the Lyapunov stability condition.

---

## The Lyapunov Stability Condition

If there exists a matrix $$P$$ such that

$$
P>0
$$

and

$$
A^TP+PA<0,
$$

then the system is asymptotically stable.

This result is one of the most important theorems in control theory and forms the foundation of modern Lyapunov analysis.

---

## Why Is This an LMI?

The inequality

$$
A^TP+PA<0
$$

is called a **Linear Matrix Inequality (LMI)**.

To understand why, note that:

* $$A$$ is known.
* $$P$$ is unknown.
* Every entry of $$A^TP+PA$$ depends linearly on the entries of $$P$$.

There are no products between unknown variables and no nonlinear terms involving $$P$$.

Because the matrix expression is linear in the unknown matrix $$P$$, the condition is an LMI.

This is one of the earliest and most important LMIs in control theory.

---

## Solving the Lyapunov Inequality

Instead of solving

$$
A^TP+PA<0
$$

directly, a common approach is to choose any positive definite matrix

$$
Q>0
$$

and solve the Lyapunov equation

$$
A^TP+PA=-Q.
$$

Since $$Q$$ is known, this becomes a system of linear equations in the entries of $$P$$.

A common choice is

$$
Q=I,
$$

which gives

$$
A^TP+PA=-I.
$$

If the resulting solution $$P$$ is positive definite, then the system is stable.

---

## Worked Example

Consider

$$
A =
\begin{bmatrix}
-1 & 0 \
0 & -2
\end{bmatrix}
$$

and choose

$$
Q= I=
\begin{bmatrix}
1 & 0 \
0 & 1
\end{bmatrix}.
$$

Assume

$$
P=
\begin{bmatrix}
p_{11} & p_{12} \
p_{12} & p_{22}
\end{bmatrix}.
$$

Substituting into

$$
A^TP+PA=-I
$$

gives

$$
\begin{bmatrix}
-2p_{11} & -3p_{12} \
-3p_{12} & -4p_{22}
\end{bmatrix}
=
\begin{bmatrix}
-1 & 0 \
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

Therefore,

$$
P=
\begin{bmatrix}
0.5 & 0 \
0 & 0.25
\end{bmatrix}.
$$

Since both eigenvalues are positive, $$P$$ is positive definite.

Therefore, the system is asymptotically stable.

---

## Why LMIs Became So Important

The Lyapunov inequality was originally developed as a stability test, but researchers later discovered that many control design problems could be written in a similar form.

Examples include:

* Stability analysis
* State-feedback controller design
* Observer design
* Robust control
* Gain scheduling
* Model Predictive Control (MPC)
* $$H_{\infty}$$ control

The key advantage is that LMIs define **convex optimization problems**.

Convex optimization is particularly attractive because every local optimum is also a global optimum.

Unlike many nonlinear optimization problems, convex problems can be solved efficiently and reliably using modern semidefinite programming solvers.

As computing power increased during the 1990s and 2000s, LMIs became one of the central mathematical tools in control engineering and optimization.

Today, many advanced control algorithms can be viewed as extensions of the same idea that Lyapunov introduced more than a century ago.

---

## Final Thoughts

The simple condition

$$
A^TP+PA<0
$$

may look like just another matrix inequality, but it represents one of the most influential ideas in control theory.

What began as Lyapunov's method for proving stability evolved into an entire framework for controller design and optimization.

Today, LMIs form the mathematical backbone of many advanced control techniques, connecting classical stability theory with modern convex optimization.

If you study modern control theory, optimization, MPC, robust control, or semidefinite programming, you will encounter LMIs repeatedly. Understanding the Lyapunov inequality is therefore one of the best starting points for learning the field.

---

## References

[1] Stephen Boyd, Laurent El Ghaoui, Eric Feron, and V. Balakrishnan, *Linear Matrix Inequalities in System and Control Theory*.

https://stanford.edu/~boyd/lmibook/lmibook.pdf

[2] Stephen Boyd, Laurent El Ghaoui, Eric Feron, and V. Balakrishnan, *A History of LMIs in Control Theory*.

https://web.stanford.edu/~boyd/papers/pdf/history_lmi_ctrl.pdf

[3] CVXGEN Documentation

https://cvxgen.com/docs/index.html
