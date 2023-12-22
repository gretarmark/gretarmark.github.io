---
layout: post
title: Kalman Filter
published: true
---

The Kalman Filter is an algorithm employed for estimating the state variables of a dynamic system. Dr. Rudolph E. Kalman developed this algorithm during the late 1950s and early 1960s. While it shares roots with the Wiener Filter, Kalman's significant contribution lies in connecting the state estimation problem with state-space models, as well as the fundamental concepts of controllability and observability.

A very clear explanation of the Kalman Filter is described by Roger Labbe in [1]. The Kalman Filter is also introduced in [3].

Kalman Filters include three important informations (four with past and present estimated values):

* **Estimation:** Past value $$\hat{x}_{t-1}$$ and present value $$\hat{x}_{t}$$
* **Prediction:** $$x_t$$ is found from previous sample.
* **Measurement:** Present value $$z_t$$

We can calculate new estimated value and add a constant scaling factor for the predicted value ($$x_{gain}$$) which has to be chosen carefully:

$$
\hat{x}_t = x_t + x_{gain}(z_t - x_t)
$$

The difference $$z_t - x_t$$ is called the *residual*. The estimated values always end up being between the measurement and the prediction as shown in [1] in chapter 1.1.

Key facts of the Kalman Filter:
* If we only use estimates from the measurement then the prediction will not affect the result.
* If we only use estimates from the prediction then the measurement will be ignored.
* We need to take **blend of the prediction and measurement**.

At every sample $$t$$ we have a previous estimate given by $$\hat{x}_{t-1}$$ and a present measurement $$z_t$$ and a present prediction $$x_t$$ which forms new estimate $$\hat{x}_{t}$$.  



#### References

<!--[1] Kalman Filter. [Link to reference](https://drive.google.com/file/d/0By_SW19c1BfhSVFzNHc0SjduNzg/view?resourcekey=0-41olC9ht9xE3wQe2zHZ45A)-->

[1] Roger Labbe. Kalman Filter. [Link to reference](https://github.com/rlabbe/Kalman-and-Bayesian-Filters-in-Python)

[2] Carl Wunsch. MIT. [Link to reference](https://ocw.mit.edu/courses/12-864-inference-from-data-and-models-spring-2005/e19a413bc30bbe2976a88f4e57930df5_tsamsfmt2_6.pdf)

[3] Control System Advanced Methods. The Control Handbook 2nd ed. William S. Levine. [Link to reference](https://www.amazon.com/Control-Systems-Handbook-Electrical-Engineering/dp/1420073648)
