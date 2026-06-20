---
layout: post
title: "The Positive Real (PR) Lemma: Bridging Frequency-Domain and State-Space Analysis"
date: 2026-06-20
categories: [control-theory, optimization, lmi]
tags: [control-theory, kyp-lemma, positive-real, passivity, lyapunov, lmi]
description: "Learn the Positive Real (PR) Lemma, also known as the Kalman–Yakubovich–Popov (KYP) Lemma, and how it connects frequency-domain analysis, passivity, Lyapunov theory, and LMIs."
published: true
---

The **Positive Real (PR) Lemma**, also known as the **Kalman–Yakubovich–Popov (KYP) Lemma**, is one of the most important results in modern control theory.

It establishes a powerful connection between:

* Frequency-domain analysis
* State-space analysis
* Lyapunov theory
* Linear Matrix Inequalities (LMIs)

In many ways, the PR Lemma plays a role similar to the Separation Principle: it creates a bridge between two fundamentally different viewpoints of dynamical systems.

---

# What Does "Positive Real" Mean?

A transfer function (G(s)) is called **positive real** if:

1. (G(s)) is analytic in the open right-half plane ((\Re(s) > 0))
2. For all (s) satisfying (\Re(s) > 0),

[
G(s)+G^*(s)\geq0
]

where (G^*(s)) denotes the complex conjugate transpose.

For a SISO system, this condition simplifies to:

[
\Re{G(j\omega)}\geq0
]

for all frequencies (\omega).

---

# Example

Consider the transfer function

[
G(s)=\frac{1}{s+1}.
]

Evaluating at (s=j\omega),

[
G(j\omega)=\frac{1}{1+j\omega}.
]

Multiplying numerator and denominator by the complex conjugate gives

[
G(j\omega)=\frac{1-j\omega}{1+\omega^2}.
]

The real part is therefore

[
\Re{G(j\omega)}
===============

\frac{1}{1+\omega^2}

> 0.
> ]

Since the real part is positive for every frequency, the system is positive real.

---

# Why Is Positive Realness Important?

Positive real systems arise naturally in:

* Passive systems
* Electrical circuits
* Mechanical systems
* Robust control
* Adaptive control
* Energy-based control methods

A positive real system cannot generate net energy.

Examples include:

* Resistors
* Spring-damper systems
* Passive electrical networks

These systems may store or dissipate energy, but they cannot create energy.

---

# State-Space Representation

Consider the linear system

[
\dot{x}=Ax+Bu
]

[
y=Cx+Du.
]

Its transfer function is

[
G(s)=C(sI-A)^{-1}B+D.
]

To verify positive realness directly, we would need to check

[
\Re{G(j\omega)}\geq0
]

for every frequency (\omega).

Since there are infinitely many frequencies, this becomes a difficult frequency-domain problem.

The PR Lemma transforms this problem into a matrix inequality.

---

# The Positive Real Lemma

Assume:

* ((A,B,C)) is a minimal realization
* (A) is Hurwitz (internally stable)

Then the transfer function (G(s)) is positive real **if and only if** there exists a symmetric matrix

[
P=P^T>0
]

such that

[
\begin{bmatrix}
A^TP+PA & PB-C^T \
B^TP-C & -(D+D^T)
\end{bmatrix}
\leq0.
]

This condition is a **Linear Matrix Inequality (LMI)**.

---

# Worked Example

Consider the first-order system

[
\dot{x}=-x+u
]

[
y=x.
]

The state-space matrices are

[
A=-1,\qquad
B=1,\qquad
C=1,\qquad
D=0.
]

The transfer function is

[
G(s)=\frac{1}{s+1}.
]

Earlier, we verified directly from the frequency response that this transfer function is positive real.

Now let us verify the same result using the PR Lemma.

The PR LMI becomes

[
\begin{bmatrix}
A^TP+PA & PB-C^T \
B^TP-C & -(D+D^T)
\end{bmatrix}
=============

\begin{bmatrix}
-2P & P-1 \
P-1 & 0
\end{bmatrix}
\leq0.
]

Choose

[
P=1.
]

Substituting gives

[
\begin{bmatrix}
-2 & 0 \
0 & 0
\end{bmatrix}
\leq0.
]

The matrix is negative semidefinite because its eigenvalues are

[
-2,\qquad 0.
]

Since

[
P=1>0
]

and the LMI is satisfied, the PR Lemma confirms that the system is positive real.

Notice what happened:

* The frequency-domain verification required checking all frequencies.
* The PR Lemma required finding a single positive-definite matrix (P).

This illustrates the power of the theorem.

---

# Why Is This Remarkable?

Without the PR Lemma, positive realness requires checking

[
\Re{G(j\omega)}\geq0
]

for infinitely many frequencies.

With the PR Lemma, the problem becomes:

> Find a matrix (P) satisfying a finite-dimensional LMI.

This converts an infinite frequency-domain verification problem into a convex optimization problem that can be solved efficiently using modern LMI solvers.

---

# Relationship to Lyapunov's Stability Theorem

Recall Lyapunov's stability condition:

[
A^TP+PA<0.
]

Notice that the upper-left block of the PR LMI is exactly the Lyapunov inequality.

[
A^TP+PA
]

appears directly inside the larger matrix.

This is not a coincidence.

The PR Lemma can be viewed as an extension of Lyapunov theory that incorporates:

* Inputs
* Outputs
* Energy exchange

rather than focusing solely on internal stability.

---

# Connection to Passivity

The PR Lemma is closely related to the concept of passivity.

Define a quadratic storage function

[
V(x)=x^TPx.
]

Using the PR Lemma, one can show that

[
\dot{V}(x)\leq u^Ty.
]

The interpretation is straightforward:

* (V(x)) represents stored energy.
* (u^Ty) represents supplied power.

The inequality states that the rate of increase of stored energy cannot exceed the power entering the system.

This is precisely the definition of a passive system.

---

# Physical Interpretation

Imagine a spring-damper system.

The spring stores energy, while the damper dissipates energy.

If external forces stop acting on the system, the stored energy eventually decreases.

The system never produces additional energy on its own.

This behavior is exactly what the PR Lemma characterizes mathematically.

---

# Why Control Engineers Love the PR Lemma

The KYP/PR Lemma serves as a foundation for many important areas of modern control theory:

* Passivity-based control
* Adaptive control
* Robust control
* Dissipativity theory
* Integral Quadratic Constraints (IQCs)
* (H_\infty) control
* Modern LMI methods

Many advanced control results can ultimately be traced back to extensions of the KYP Lemma.

---

# Big Picture

Three landmark results help define modern control theory:

| Result                    | Connects                             |
| ------------------------- | ------------------------------------ |
| Lyapunov Theorem          | Stability ↔ Matrix Inequality        |
| Positive Real (KYP) Lemma | Frequency Response ↔ State-Space LMI |
| Separation Principle      | State Feedback ↔ Observer Design     |

The Positive Real Lemma is often regarded as one of the deepest results in control theory because it unifies two powerful perspectives:

* Frequency-domain methods (Nyquist, Bode, positive realness)
* State-space methods (Lyapunov functions and LMIs)

By transforming an infinite frequency-domain condition into a finite-dimensional matrix inequality, the PR Lemma provides one of the most elegant bridges between classical and modern control theory.

---

# Key Takeaway

The Positive Real (KYP) Lemma states that a transfer function is positive real if and only if there exists a positive-definite matrix (P) satisfying a particular LMI. This remarkable result connects frequency-domain properties, Lyapunov theory, passivity, and convex optimization, making it one of the cornerstones of modern control engineering.
