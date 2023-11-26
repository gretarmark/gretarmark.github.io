---
layout: post
title: Ampere's Law
published: true
---

In today's post I want to talk about Ampere's law and how to find the magnitude of the magnetic field around a wire.

Ampere's law states that if $$\mathcal{C}$$ is a closed curve in the space around a wire that conducts current $$I$$, then

$$\int_{\mathcal{C}} {\bf B} \cdot d{\bf r} = kI$$

where $${\bf B}$$ is the magnetic field produced by the current $$I$$, and $$k$$ is a constant. 

If the wire is long, thin and straight, and $$\mathcal{C}$$ is a circle centered in the center of the wire that lays in a plane that is perpendicular to the wire, then the magnetic field $$\bf B$$ is tangent to the circle and its magnitude is the same everywhere around the circle. The direction of the magnetic field is determined by the right hand rule. 

The magnitude of the magnetic field $$\bf B$$ with radius $$r$$ away from the center of the wire can be determined by Ampere's law

![Fig 1]({{ site.baseurl }}/images/AmperesLaw_fig1.png "zero order"){:width=75%}  
**Figure 1: Magnetic field around a straight wire. The wire lies along the z-axis.**

In figure 1, the wire lies along the z-axis and the current $$I$$ is traveling in along the wire in the direction of positive z, represented as $$\bar k$$. Using the right-hand rule, we can see that the magnetic field is traveling counter clock wise around the wire in the xy-plane.

Notice that we integrate over the magnetic field $$\bf B$$ and in each step we only take a tiny little bit of the parametric curve of the magnetic field, therefore we need to find a parametrization of the magnetic field.

It can also be seen that the vector of the magnetic field is tangent vector on the curve $$\mathcal{C}$$ which is enveloped around the wire and that the tangent vector $$\bf B$$ is parallel to the velocity vector. Therefore, the angle between these two vectors is going to be $$0^{\circ}$$ and $$\cos(0) = 1$$, and the length of the curve around the wire is $$2\pi$$.

To parameterize the curve $$\mathcal{C}$$ around the wire, we can use cylindrical coordinates to get

$$\bar{r}(t) = r\cos(t)\hat{i} + r\sin(t)\hat{j} + z \hat{k} \qquad \quad 0 \leq t \leq 2\pi$$

Now we can see that we can integrate the curve over an interval. We can use line integral of tangential component of $$\bf B$$ along the curve $$\mathcal{C}$$

## Theorem:

Let $${\bf F}(x,y)$$ be a vectorfield and $${\bf r}:[a,b] \rightarrow \mathbb{R}^2$$ be a parametrization on the curve $$\mathcal{C}$$ and let's assume that the parametric curve $$\bf r$$ is continuously differentiable by sections. The integral of the vectorfield $${\bf F}(x,y)$$ along the curve $$\mathcal C$$ is defined as

$$\int_{\mathcal C} {\bf F} \cdot d {\bf r} = \int_{\mathcal{C}} {\bf F} \cdot {\bf T} d{\bf s} = \int_a^b {\bf F}({\bf r}(t)) \cdot {\bf r}^{'}(r) \, dt.$$

From the theorem above, we can use

$$\int_{\mathcal{C}}{\bf F} d{\bf r} = \int_{a}^{b} {\bf F}({\bf r}(t)) \cdot {\bf r}^{'}(r) dt$$

so we get

$$\int_{\mathcal{C}}{\bf B} d{\bf r} = \int_{0}^{2\pi} {\bf B}({\bf r}(t)) \cdot {\bf r}^{'}(r) \, dt$$

By looking at the vector $$\bf B$$ in figure 1 above, we can see that this is the length $$\vert B \vert$$  multiplied by the unit tangent vector $$\bf T$$. The equation for a unit tangent vector is 

$${\bf T} = \frac{ {\bf r}^{'}(t) } { \vert {\bf r}^{'}(t) \vert}$$

now we can see that

$${\bf B} = \vert B \vert \cdot {\bf T} = \vert B \vert \cdot \frac{r^{'}(t)}{ \vert r^{'}(t) \vert }$$

and we get

$$\int_{\mathcal{C}} {\bf B} \cdot d{\bf r} = \int_0^{2\pi} {\bf B}({\bf r}(t)) \cdot {\bf r}^{'} dt $$ 
 
$$ \= \int_0^{2\pi} \vert B \vert \cdot \frac{r^{'}(t)}{\vert r^{'}(t) \vert} \cdot {\bf r}^{'}(t) dt$$ 

