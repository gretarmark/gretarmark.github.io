---
layout: post
title: Ode45 functions in Matlab
---

The ode45 function in Matlab is used to solve nonstiff differential equations. The function is based on an explicit Runge-Kutta (4,5) method.

ODE problems are usually divided into "stiff" and "non-stiff" problems. "non-stiff" problems are easier to solve and are quiet common, they are usually solved using methods like explicit Runge-Kutta. "stiff" problems are harder to solve numerically and require more computational effort. A common method is implicit Runge-Kutta.

#### References
[1] Matlab Documentations. <https://se.mathworks.com/help/matlab/ref/ode45.html>

[2] Kidger, Patrick, "How to choose a solver, Diffrax" <https://docs.kidger.site/diffrax/usage/how-to-choose-a-solver/#:~:text=%22Stiffness%22%20generally%20refers%20to%20how,implicit%20Runge%2D%2DKutta%20methods.>

[3] Douglas, Brian. “Control System Lectures - Bode Plots, Introduction.” <https://www.youtube.com/watch?v=_eh1conN6YM&list=PLUMWjy5jgHK1NC52DXXrriwihVrYZKqjk&index=9> Visited on 08/14/2019. 

[4] Cheever, Erik. “Bode Plots Overview.” <https://lpsa.swarthmore.edu/Bode/Bode.html> Visited on 08/15/2019.
