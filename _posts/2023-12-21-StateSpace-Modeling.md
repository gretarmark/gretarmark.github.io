---
layout: post
title: State Space Models
published: false
---

State Space Models

## Forming First Order Equations from Higher Order Equations

Many models of physical systems require second or higher order differential equations with control input u:

an
d
ny
dtn
+ an−1
d
n−1y
dtn−1
+ · · · + a2
d
2y
dt2
+ a1
dy
dt + a0 = u

State-space methods require first-order equations. Any higher order system of equations can be reduced
to first-order by defining extra variables for the derivatives and then solving.
Let’s do an example. Given the system x ̈ − 6  ̇x + 9x = u find the equivalent first order equations. I’ve
used the dot notation for the time derivatives for clarity.
The first step is to isolate the highest order term onto one side of the equation.

x ̈ = 6  ̇x − 9x + u

We define two new variables:

x1(u) = x
x2(u) =  ̇x

Now we will substitute these into the original equation and solve. The solution yields a set of first-order
equations in terms of these new variables. It is conventional to drop the (u) for notational convenience.
We know that x ̇ 1 = x2 and that x ̇ 2 =  ̈x. Therefore
x ̇ 2 =  ̈x
= 6  ̇x − 9x + t
= 6x2 − 9x1 + t

Therefore our first-order system of equations is
x ̇ 1 = x2
x ̇ 2 = 6x2 − 9x1 + t

If you practice this a bit you will become adept at it. Isolate the highest term, define a new variable and
its derivatives, and then substitute.

#### References

[1] Kalman Filter. [Link to reference](https://drive.google.com/file/d/0By_SW19c1BfhSVFzNHc0SjduNzg/view?resourcekey=0-41olC9ht9xE3wQe2zHZ45A)

[2] Kalman Filter. [Link to reference](https://github.com/rlabbe/Kalman-and-Bayesian-Filters-in-Python)
