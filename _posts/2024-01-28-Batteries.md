---
layout: post
title: Batteries
published: true
---

When choosing a battery for some electronic devices, it is crucial to know how to read the imformation given on the various types of batteries out there.

Let's say we are going to buy a battery for a drone. The given information of the battery in figure 1 below is
* 4000mAh
* 30-40c discharge
* 2 cell 7.4V
* LiPo (Lithium-Polymer Ion)

![Fig 1]({{ site.baseurl }}/images/Battery/Battery_1.png "zero order"){:width=75%}  
**Figure 1: Example of a battery.**

4000 mAh tells you how much capacity the battery have. The greater the capacity of the battery is, the heavier it become. Battery rated at 4000mAh can deliver 4000mA of current for one hour, or 2000mA for two hours and so forth. A higher milli amper hour rating means a battery can power a device that requires more energy or can power a device for a longer time.

30-40c means that the battery has the ability to provide continuous current at 30 times c. "c" can be thought of as a variable and is calculated as follows

$$\\
\begin{align}
c &= \frac{\text{Capacity of the battery}}{10^3}   \tag{1.1} \\
&= \frac{4000 \, mAh}{1000} = 4A \tag{1.2}
\end{align}
\\$$

This is called the c rating (c stands for "capacity") of the battery, it doesn't matter how many cells it has. The c is not dependent on the amount of cells.
Now that we have that number, we can calculate how much current this battery can provide continuously and how much current this battery can provide in burst. Let's calculate that
The continuous capability of this battery to provide current is according to the rating of the battery on the sticker is

$$\\
\begin{align}
30 \cdot c = 30 \cdot 4 = 120A   \tag{1.3} \\
40 \cdot c = 40 \cdot 4 = 160A   \tag{1.4}
\end{align}
\\$$

A small pack like this can provide a 120A - 160A of current continuously until it discharges, but we don't normally draw that much power. If we did, the leads will just melt and anything else pretty much. A battery like this gives plenty of energy and output capacity to operate machines like for example drones. 

If you're doing high performance flying like drone racing, you'll want a battery with a high c rating. These flights require a lot of power quickly, so a high discharge rate is beneficial. Higher c rating batteries can often be larger and heavier, which can affect the drone's flight time and maneuverability.

The battery plugs are called "JST XH" and "bullet plugs".
LiPO batteries are not batteries where you can buy a cheap charger for. These batteries needs a bit more care than other batteries.
It needs a high quality balanced charger, for example "Powertech Plus". Make sure you purchase it from a reputable store. 
A balanced charger is needed to be able to charge the two cells in a balanced way. An imbalanced charge would be if one cell is charged 3.7 V and the other 4.3 V, which we don't want.

The battery has two 3.7 V cells. The nominal voltage is in total $$2\cdot 3.7V = 7.4 \, V$$.  

Common types of batteries used in quadcopters are
* Nickel-Cadmium (NiCd)
* Nickel-Metal Hydride (NiMH)
* Lithium-Ion (Li-ion)
* Lithium Polymer (LiPo)

