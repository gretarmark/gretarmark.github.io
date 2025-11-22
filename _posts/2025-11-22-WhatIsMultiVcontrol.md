---
layout: post
title: What is Multivariable Control?
published: true
---

Multivariable control refers to controlling systems with more than one input or more than one actuator.
Unlike single-input controllers, multivariable control methods such as LQR and MPC must handle interactions between actuators and states.
This requires designing a control law that coordinates all actuators simultaneously rather than treating each one independently.

To form a mathematical rule (or law) that coordinates multiple actuators using multivariable control methods e.g. LQR or MPC, 
you need to follow a structured control-design process.

### 1. Start with a State-Space Model

For a system with multiple actuators, the dynamics are described by

$$\dot{x}(t) = Ax(t) + Bu(t)$$

or in discrete time

$$\dot{x}_{k+1} = Ax_{k} + Bu_{k}$$

Here, $$x$$ contains all relevant states (positions, velocities, pressures, currents, etc.), and $$u$$ contains the inputs for each actuator.
Any coupling between actuators is captured naturally inside the matrices $$A$$ and $$B$$.

### 2. Define the Control Objective

LQR and MPC both use an optimization problem where the “goal” of the controller is encoded in a cost function. 
This is exactly where you define how actuators should work together.

For LQR, the cost is

$$J = \int_0^{\infty} (x^T Q x + u^T R u)\, dt$$

and for MPC

$$J = \sum_{k=0}^{N_p} (x_k^{T}Qx_k + u_k^{T}Ru_k)$$

### 3. The Mathematical Rule Between Actuators Is Encoded in Q and R

If you want actuators to behave similarly or follow a specific relation, you add penalties on their differences.

Eample rule:

Actuator 1 and actuator 2 should apply nearly the same input.

Add the term

$$(u_1 - u_2)^2$$

This creates a coupling in the R matrix and forces the controller to keep both actuators coordinated.
The controller will automatically satisfy this rule while still optimizing performance.

### 4. LQR: Compute the Control Law

Solve the algebraic Riccati equation to obtain the feedback gain $$K$$,

$$u = -Kx$$

The rows of $$K$$ determine how each actuator reacts to all system states.
If the rows are similar, the actuators naturally coordinate.

### 5. MPC: Optimization With Constraints

MPC minimizes the same style of cost function but also allows constraints.
This means actuator relationships can be defined either as:

- Soft rules (penalties, like $$(u_1 - u_2)^2$$). Soft rules influence behavior but do not strictly force it. They are encoded in Q and R.
- Hard constraints (e.g., $$u_1 = u_2$$, or $$\vert u_1 - u_2 \vert \leq \epsilon$$). 

MPC enforces these rules while predicting the future behavior of the system.

# Summary

- The “mathematical rule” between actuators is created by how you structure the cost function.
- LQR encodes the rule inside the $$Q$$ and $$R$$ matrices, which shape the feedback gain $$K$$.
- MPC enforces the rule through penalties and constraints during the optimization.
- Both methods require a state-space model of the system.

<!--
## Conclusion

The magnitude of the magnetic field around a wire is inversely proportional to the distance from the wire, with the field strength decreasing as the distance from the wire increases.

-->
#### References
[1] Robert Adams & Christopher Essex. Calculus, A Complete Course, 9th edition.
