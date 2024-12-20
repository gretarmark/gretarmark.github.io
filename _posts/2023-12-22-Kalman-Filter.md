---
layout: post
title: Kalman Filter
published: false
---

The Kalman Filter is an algorithm employed for estimating the state variables of a dynamic system. Dr. Rudolph E. Kalman developed this algorithm during the late 1950s and early 1960s. While it shares roots with the Wiener Filter, Kalman's significant contribution lies in connecting the state estimation problem with state-space models, as well as the fundamental concepts of controllability and observability.

A very clear explanation of the Kalman Filter is described by Roger Labbe in [1]. The Kalman Filter is also introduced in [3].

Kalman Filters include three important informations (four with past and present estimated values):

* **Estimation:** Past value $$\hat{x}_{t-1}$$ and present value $$\hat{x}_{t}$$.
* **Prediction:** $$x_t$$ is found from previous sample.
* **Measurement:** Present value $$z_t$$.

We can calculate new estimated value and add a constant scaling factor for the predicted value ($$g$$) which has to be chosen carefully:

$$
\hat{x}_t = x_t + g \cdot (z_t - x_t)
$$

The difference $$z_t - x_t$$ is called the *residual*. The estimated values always end up being between the measurement and the prediction as shown in [1] in chapter 1.1.

Key facts of the Kalman Filter:
* If we only use estimates from the measurement then the prediction will not affect the result.
* If we only use estimates from the prediction then the measurement will be ignored.
* We need to take **blend of the prediction and measurement**.

At every sample $$t$$ we have a previous estimate given by $$\hat{x}_{t-1}$$ and a present measurement $$z_t$$ and a present prediction $$x_t$$ which forms new estimate $$\hat{x}_{t}$$.  

For g-h filter as in chapter 1.1 in [1], it is important to choose the initial value for the prediction very well because the further the predicted values are away from the measurements the greater the gap between the values will be, and the estimated values are always between these two values, so bad prediction will result in worse filtering. Filter like that, where you need to correctly guess a rate of change (prediction) is not very useful. Even if the initial guess is correct, the filter will fail as soon as that predicted rate of change changes.

It is better to update the prediction in every step by using e.g. two noisy measurements instead of using a guess. Data is better than a guess. We should never throw information away, instead we should use it although we get two bad measurements, because again, data is better than a guess.  
A new gain $$x_{gain}$$ can be calculated in each step using

$$
x_{new,gain} = x_{old,gain} + h \cdot \frac{z_t - x_t}{dt}
$$

where $$h$$ is a scaling factor. By using this feature, it can take few samples for the filter to accurately predict the values being measured. In both the equations above, there were no methodology used to choose the scaling factors of $$g$$ and $$h$$. The filter above is called $$g-h$$ filter or $$\alpha-\beta$$ filter.

The g-h filter is the basis for many filters, including Kalman Filter. The Kalman Filter will vary these two factors $$g$$ and $$h$$ dynamically at each time step.

* Multiple data points are more accurate than one data point, so throw nothing away no matter how inaccurate it is.
* Always choose a number part way between two data points to create a more accurate estimate.
* Predict the next measurement and rate of change based on the current estimate and how much we think it will change.
* The new estimate is then chosen as part way between the prediction and next measurement scaled by how accurate is.

* The system (the plant) is the object we want to estimate, we would maybe want to estimate the weight or the orientation of the object. 
* The state of the system is the current configuration or values of that system that is of interest.
* The measurement is a measured value of the system. Measurements can be inaccurate, so it may not have the same value as the state.
* The state estimate is the filter's estimate of the state.
* The state should be understood as the actual value of the system. This value is usually *hidden* to us. If I stepped on a scale you'd then have a measurement. We call this *observable* since you can directly observe this measurement. In contrast, you can never directly observe weight, you can only measure it.
* Any estimation problem consists of forming an estimate of a hidden state via observable measurements. If you read the literature these terms are used when defining a problem, so you need to be comfortable with them.


<!--
Here is the literature recommendation and the learning path for "quickly" and correctly learning the Kalman filter algorithm. The Kalman filter is actually a "simple" recursive least squares method that is propagated through the state-space model. Here are the five learning steps and the recommended book chapters.

STEP 1: First, learn what is a batch least squares method and how this method is used to solve parameter estimation problems.

-> Section 2.6: "Linear least-squares problems" in "Filtering and System Identification", by M. Verhaegen and V. Verdult.

STEP 2: Then, learn how to implement the batch least squares method in a recursive manner. That is, learn what is a recursive least squares method.

->Section 3.3 in "Optimal State Estimation" by Dan Simon.

STEP 3: Then, learn how the covariance matrices are propagated through linear state-space models.

-> Section 4.1 in "Optimal State Estimation" by Dan Simon.

STEP 4: Learn how to derive the Kalman filter by using the recursive least squares method from STEP 2 and by propagating covariance matrices from STEP 3.

-> Section 5.1 in "Optimal State Estimation" by Dan Simon.

STEP 5: Learn what is an alpha-beta-gamma tracking filter. This is basically a Kalman filter for tracking objects. Try to implement this filter and a numerical example in Python/MATLAB.

-> Section 7.3.2 in in "Optimal State Estimation" by Dan Simon.
-->

#### References

<!--[1] Kalman Filter. [Link to reference](https://drive.google.com/file/d/0By_SW19c1BfhSVFzNHc0SjduNzg/view?resourcekey=0-41olC9ht9xE3wQe2zHZ45A)-->

[1] Roger Labbe. Kalman Filter. [Link to reference](https://github.com/rlabbe/Kalman-and-Bayesian-Filters-in-Python)

[2] Carl Wunsch. MIT. [Link to reference](https://ocw.mit.edu/courses/12-864-inference-from-data-and-models-spring-2005/e19a413bc30bbe2976a88f4e57930df5_tsamsfmt2_6.pdf)

[3] Control System Advanced Methods. The Control Handbook 2nd ed. William S. Levine. [Link to reference](https://www.amazon.com/Control-Systems-Handbook-Electrical-Engineering/dp/1420073648)
