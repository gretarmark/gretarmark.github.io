---
layout: post
title: Quadratic Programming
published: true
---

The quadratic programming is about minimizing the quadratic form 

$$\\
\begin{align}
f({\bf x}) = \frac{1}{2} {\bf x}^T{\bf A}{\bf x} + {\bf x}^T{\bf b}  \tag{1.1}
\end{align}
\\$$

$${\bf A}$$ has to be positive definite so there exist a minimal solution. If it's not positive definite, there is no minimum solution.
$${\bf A}$$ is a matrix, $${\bf x}$$ and $${\bf b}$$ are vectors. 

Let's try to understand why this quadratic form is used as it is in minimization problems.
Let's consider the function

$$\\
\begin{align}
f(x) = x^2 \tag{1.2}
\end{align}
\\$$

It's easy to find the minimum at function 1.2. It's a convex function and the minimum value is at 0.
Now let's make this function a little bit less boring by shifting it a little bit, adding the term $$-bx$$ to it

$$\\
\begin{align}
f(x) = x^2 - bx \tag{1.3}
\end{align}
\\$$

and even making it a bit more interesting by scaling the $$x^2$$ term by a scaling factor $$a$$

$$\\
\begin{align}
f(x) = ax^2 - bx \tag{1.4}
\end{align}
\\$$

The minimum of function 1.4 is found by finding the derivative of it and solve for 0 

$$\\
\begin{align}
\frac{df(x)}{dx} = \frac{d}{dx}(ax^2 - bx) = 2ax - b \tag{1.5}
\end{align}
\\$$

the minimum is at

$$\\
\begin{align}
2ax - b &= 0 \\
x &= \frac{b}{2a} \tag{1.6}
\end{align}
\\$$

but we want to get a little bit nicer solution, so we add $$1/2$$ to equation 1.4

$$\\
\begin{align}
f(x) = \frac{1}{2}ax^2 - bx \tag{1.7}
\end{align}
\\$$

Now let's see how the derivative of eq. 1.7 looks like and find the minimum value

$$\\
\begin{align}
\frac{df(x)}{dx} = \frac{d}{dx}\left(\frac{1}{2}ax^2 - bx\right) = ax-b   \tag{1.8}
\end{align}
\\$$

the minimum value of eq. 1.8 is at

$$\\
\begin{align}
ax-b &= 0 \\
ax &= b \\
x &= \frac{b}{a} \tag{1.9}.
\end{align}
\\$$

This solution is much more straight forward and simpler.







