---
layout: post
title: Root Mean Square
published: true
---

Root Mean Square (RMS) [1] is a mathematical method used widely in science and engineering. When finding the average value of a function that have both positive and negative values, it will not show the true average value. Therefore it is necessary to square the signal and take the square root of it, that's what RMS is about.

Phil have already talked about this topic on his You Tube channel [2], but I want to take it a bit further and show how it is used in control theory. 

AC signals in the socket in your wall is a sine wave that have both positive and negative parts. A simple sine wave is given by

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

<!--From this, let's move on to control theory and take a look at how it is used there. 

In optimal control, the quadratic cost function 
-->



#### References

[1] "Root-Mean-Square." Wikipedia. Visited 3 Dec 2023. [Link to reference](https://en.wikipedia.org/wiki/Root_mean_square)

[2] "Recursive RMS (STM32 Implementation) - Phil's Lab #103". [Link to reference](https://www.youtube.com/watch?v=miUXBXUDJDI&t=188s)
