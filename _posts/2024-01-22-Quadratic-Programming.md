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

This solution looks a bit better and is the simplest interesting function that has a minimum. It's good practice to always look for the simplest problem to solve.

Equation 1.1 have both quadratic part and a linear part. $$\frac{1}{2} {\bf x}^T{\bf A}{\bf x}$$ is the quadratic part and $${\bf x}^T{\bf b}$$ is the linear part.
We can say that we have a quadratic form with a linear shift in eq. 1.1 just so the minimum is not at 0. If there would not be a shift  
Again, $${\bf A}$$ must be positive definite, there cannot possibly be a minimum if $${\bf A}$$ is not positive definite. 

Let's recall what least-squares is. It's about finding the best approximate solution for $${\bf Ax} = {\bf b}$$, that solution is called the least-squares solution.
It can be seen that the minimum solution of the quadratic problem above looks exactly the same as the least-squares solution.

We can see for example, if we have

$$\\
\begin{align}
f(x,y,z) = \frac{1}{2} \begin{bmatrix} x & y & z \end{bmatrix} \begin{bmatrix} 4 & 1 & 2 \\ 1 & 8 & 5 \\ 2 & 5 & 4 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} - \begin{bmatrix} x & y & z \end{bmatrix} \begin{bmatrix} 2 \\ 3 \\ 4 \end{bmatrix} \tag{1.10}.
\end{align}
\\$$

and we solve this matrix form, we get

$$\\
\begin{align}
f(x,y,z) = 2x^2 + 4y^2 + 2z^2 + xy + 5yz + 2zx - 2x - 3y - 4z \tag{1.11}.
\end{align}
\\$$

the derivatives with respect to $$x,y,z$$ is

$$\\
\begin{align}
f_x = 4x + y + 2z - 2 = 0 \tag{1.12} \\
f_y = x + 8y + 5z - 3 = 0 \tag{1.13} \\
f_z = 2x + 5y + 4z - 4 = 0 \tag{1.14} 
\end{align}
\\$$

and we put this again on a matrix form

$$\\
\begin{align}
\begin{bmatrix} 4 & 1 & 2 \\ 1 & 8 & 5 \\ 2 & 5 & 4 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} x \\ y \\ z \end{bmatrix} \tag{1.15} 
\end{align}
\\$$

which takes the form $${\bf Ax} = {\bf b}$$.

This shows that the fundamental problem of Linear Algebra comes from from a minimization problem. Euler once said that there is nothing in nature that doesn't include minimization.

To solve the least-squares problem, we can minimize eq. 1.1, pick a random number x, and the go in the direction that would make the expression in eq. 1.1 smaller. We have to move in the opposite direction of the gradient. This is called the gradient decent.
The gradient in the equation $${\bf Ax} = {\bf b}$$ is the vector $${\bf Ax}$$.
What we actually do is we start with a random $${\bf x}$$ and then we replace it with $${\bf x - \alpha {\bf Ax}}$$ where $${\bf x}$$ is the current location
and $$\alpha$$ is a small step, and $${\bf Ax}$$ is the direction of the gradient. This is the most naive approach, there are much better approches that exist. This approach takes half a second to program and is called a itterative method, not as direct method as Gaussian elimination.
There is a much less naive form that works much better and is called conjugate gradient.

Post is in progress...



