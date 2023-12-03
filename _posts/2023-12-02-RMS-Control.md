---
layout: post
title: Root Mean Square
published: true
---

Root Mean Square (RMS) [1] is indeed a mathematical method widely used in science and engineering, particularly in signal processing. It is used to find the effective or "root mean square" value of a set of values, which includes both positive and negative values.

However, the primary reason for squaring the values is not necessarily to find the "true average value" but rather to eliminate the effects of the sign (positive or negative) and emphasize on the magnitude of the values. Squaring has the added benefit of making all values positive. 

The RMS value is then obtained by taking the square root of the mean (average) of the squared values. This process is useful in situations where the magnitude of a signal is more relevant than its instantaneous values. For example, in electrical engineering, RMS is often used to express the average power of an alternating current (AC).

Phil in "Phil's Lab" has already discussed this topic on his You Tube channel [2], but I wanted to delve a bit deeper and demonstrate how it is used in control theory. 

The AC signal in the socket on your wall is a sine wave that has both positive and negative parts. A simple sine wave is given by

$$f(t) = sin(t) \qquad \quad 0\leq t \leq 2\pi \qquad \qquad (1)$$

and the average value is given by

$$\bar{f} = \frac{1}{b-a} \int_a^b f(t) \, dt = \frac{1}{2\pi}\int_0^{2\pi} sin(t) \, dt = 0 \qquad \qquad (2)$$

The sine wave is plotted with a red line and the average value with a blue line in figure 1. In reality, this is not correct, we always have some energy in the AC signal, therefore the average value cannot be zero. According to [1], for AC current, the RMS is equal to the value of the constant direct current that would produce the same power dissipation in a resistive load. 

![Fig 1]({{ site.baseurl }}/images/RMS/RMS_fig1.png "zero order"){:width="80%"}  
**Figure 1: Sine wave (red) and average value (blue).**

Let's see what happens to the signal when we square it and take the square root of it. The sine wave squared is given by

$$f(t) = sin^2(t) \qquad \quad 0\leq t \leq 2\pi \qquad \qquad (3)$$

and the RMS value is denoted as

$$f_{RMS} = \sqrt{\frac{1}{b-a} \int_a^b \Big(f(t)\Big)^2 \, dt} \qquad \qquad (4)$$

In figure 2, the squared signal is plotted as a black line and the RMS value is plotted as a red line.

![Fig 2]({{ site.baseurl }}/images/RMS/RMS_fig2.png "zero order"){:width="80%"}  
**Figure 2: Squared sine wave (black) and its RMS value (red).**

From this point, let's delve into control theory and explore how it is applied. In optimal control, the quadratic cost function is calculated using similar method. From [3], a performance index is given by

$$\int_0^{\infty} |r(t) - y(t)| \, dt \qquad \qquad (5)$$

where $$r(t)$$ is a input step to a system and $$y(t)$$ is the response. The area is given by equation 5 above. This performance index is a valid function to minimize because it is limited by zero from below. However, it is easier to use a quadratic performance index of the form

$$\int_0^{\infty} (r(t) - y(t))^2 \, dt \qquad \qquad (6)$$



#### References

[1] "Root-Mean-Square." Wikipedia. Visited 3 Dec 2023. [Link to reference](https://en.wikipedia.org/wiki/Root_mean_square)

[2] "Recursive RMS (STM32 Implementation) - Phil's Lab #103". [Link to reference](https://www.youtube.com/watch?v=miUXBXUDJDI&t=188s)
