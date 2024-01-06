---
layout: post
title: Riccati Equation
published: true
---

The Algebraic Riccati Equation (ARE) for time-invariant systems is given by

$$\\

\begin{align}

{\bf 0} = {\bf A}^T {\bf P} + {\bf PA} + {\bf R}_1 - {\bf PB}{\bf R}^{-1}_2{\bf B}^T{\bf P}  

\end{align}

\\$$

* $${\bf P}$$: Unknown $$n \times n$$ symmetric matrix
* $$\bf A$$, $$\bf B$$, $${\bf R}_1$$, $${\bf R}_2$$: Known real coefficient matrices where $${\bf R}_1$$ and $${\bf R}_2$$ are symmetric

This equation may have multiple solutions, but it can be shown that only one of them is positive semi-definite (provided that the system is stabilizable) and the particular solution leads to the minimum value of the performance index:

$$\\

\begin{align}

J_{\text{min}} = \frac{1}{2} {\bf x}_0^T {\bf P}_{\infty} {\bf x}_0  

\end{align}

\\$$



<!-- https://www.youtube.com/watch?v=PKjl0kCMJ0g
    https://www.youtube.com/watch?v=dX6KyIfpVqk-->

#### References

[1] Wikipedia. [Link to reference](https://en.wikipedia.org/wiki/Algebraic_Riccati_equation)
