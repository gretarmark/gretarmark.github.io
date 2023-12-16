---
layout: post
title: Linear Programming
published: true
---

I've always been really interested in making things work efficiently, especially in designing control systems. One thing I want to talk about is Linear Programming, which is a part of optimization theory. Optimization is used in controller techniques like LQR and MPC.

---

Linear Programming is about having a optimization objective function that is linear and all the constraint equalities and the constraint inequalities are also linear.

The formulation of a Linear Programming problem is on the form

$$\\

\begin{align}

\min_{x} \quad & {\bf f}^T {\bf x} \tag{1.1}\\
\text{s.t.} \quad & {\bf Ax} \leq {\bf b} \tag{1.2}\\
& {\bf A}_{eq} {\bf x} = {\bf b}_{eq} \tag{1.3}\\
& {\bf l}_{b} \leq {\bf x} \leq {\bf u}_{b} \tag{1.4}

\end{align}

\\$$

where $$ {\bf f}^T $$ is a transposed vector of coefficients, $$\bf x$$ is a vector of the optimization variables, and these two form the objective function $${\bf f}^T {\bf x}$$. $$\min$$ stands for minimize and s.t. stands for "such that" (and "subject to").
The lower part under s.t. defines the equality and inequality constraints. $${\bf A}$$ is a matrix, $$\bf b$$ is a vector, $$ {\bf A}_{eq} $$ is a matrix, $${\bf b}_{eq}$$ is a vector, the lower and upper bounds $${\bf l}_b$$ and $${\bf u}_{b}$$ are vectors. 


Minimizing the objective function (also called cost function) is the same as maximizing the negative of it.

---

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
\begin{bmatrix} 1 & 3 & 12 \\ 3 & 2 & 3 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} = \begin{bmatrix} 20 \\ -10 \end{bmatrix} \\
\begin{bmatrix} -1200 \\ -900 \\ -1300 \end{bmatrix} \leq \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} \leq \begin{bmatrix} 1200 \\ 900 \\ 1300 \end{bmatrix}$$

which is the same as

$$
{\bf Ax} \leq {\bf b} \\
{\bf A}_{eq}{\bf x} \leq {\bf b}_{eq} \\
{\bf l}_b \leq {\bf x} \leq {\bf u}_b
$$

This can be calculated very quickly by using the linprog() function in Matlab [2]. 
The following Matlab code is used to solve the linear optimization problem above.

---

```{Matlab}
f = [2 -4 10];

A = [6  3  2 ; 3 -3  4];
b = [140 ; 60];
Aeq = [1 3 12 ; 3 2 3];
beq = [20 ; -10];
lb = [-1200 ; -900 ; -1300];
ub = [1200 ; 900 ; 1300];

options = optimoptions('linprog','Algorithm','interior-point','Display','iter',...
          'MaxIterations',1500,'OptimalityTolerance',1e-9,'ConstraintTolerance',1e-6);

[x,fval,exitflag,output] = linprog(f,A,b,Aeq,beq,lb,ub,options)
```

---

The arguments in the optimoption() function are as follows:
* 'linprog' is the solver name. It is possible to choose some other solvers [2].
* The 'Algorithm' method that is used is the 'interior-point', but it is possible to use some other methods as seen in [3]
* 'Display' and 'iter' means during the solution progress, the iteration will be displayed. We want to display:
  + 'MaxIteration': The maximum number of iterations, we don't want to go above 1500 iterations
  + 'OptimalityTolerance': We specify the optimality tolerance as 1e-9
  + 'ConstraintTolerance': Finally we specify the constraint tolerance as 1e-6 

The output is

LP preprocessing removed 0 inequalities, 1 equalities,
1 variables, and 6 non-zero elements.

 Iter            Fval  Primal Infeas    Dual Infeas  Complementarity  
    0    1.048488e+02   7.005008e+01   3.122105e+02     1.561053e+02  
    1   -1.525327e+00   3.502504e-02   1.353011e+01     6.709687e+00  
    2   -6.313812e+03   1.956677e-02   5.350381e+00     1.296430e+00  
    3   -6.316871e+03   9.783387e-06   3.916968e-04     3.960774e-02  
    4   -6.316970e+03   4.893991e-09   1.950199e-13     1.980403e-05  
    5   -6.316970e+03   4.547474e-12   4.440892e-16     9.902017e-09  
    6   -6.316970e+03   2.728484e-12   8.881784e-16     4.951009e-12  

Minimum found that satisfies the constraints.

Optimization completed because the objective function is non-decreasing in feasible directions, to within the selected value of the
function tolerance, and constraints are satisfied to within the selected value of the constraint tolerance.

<!-- https://www.youtube.com/watch?v=TqN-8fxYUYY -->

#### References

[1] Linear Programming. Wikipedia. [Link to reference](https://en.wikipedia.org/wiki/Linear_programming)

[2] Matlab. Linear Programming. [Link to reference](https://se.mathworks.com/help/optim/ug/linprog.html)

[3] Matlab. Linear Programming Algorithms. [Link to reference](https://se.mathworks.com/help/optim/ug/choosing-the-algorithm.html)
