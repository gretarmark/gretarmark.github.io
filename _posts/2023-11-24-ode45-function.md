---
layout: post
title: Ode45 functions in Matlab
published: false
---

The ode45 function in Matlab is used to solve nonstiff differential equations. The function is based on an explicit Runge-Kutta (4,5) method.

ODE problems are usually divided into "stiff" and "non-stiff" problems. "non-stiff" problems are easier to solve and are quiet common, they are usually solved using methods like explicit Runge-Kutta. "stiff" problems are harder to solve numerically and require more computational effort. A common method is implicit Runge-Kutta.

#### References
[1] Matlab Documentations. [Link to reference](https://se.mathworks.com/help/matlab/ref/ode45.html)

[2] Kidger, Patrick, "How to choose a solver, Diffrax". [Link or reference]([https://website-name.com](https://docs.kidger.site/diffrax/usage/how-to-choose-a-solver/#:~:text=%22Stiffness%22%20generally%20refers%20to%20how,implicit%20Runge%2D%2DKutta%20methods.)) 

[3] Manchester, Zak, "You Tube video, Advanced Robot Dynamics (CMU 16-715)". [Link to reference](https://www.youtube.com/watch?v=hb5rUV3rzeQ&t=707s)

[4] Brunton, Steve, "You Tube Video, Runge-Kutta Integrator Overview". [Link to reference](https://www.youtube.com/watch?v=HOWJp8NV5xU)
