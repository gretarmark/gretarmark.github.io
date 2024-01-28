---
layout: post
title: Batteries
published: false
---

When choosing a battery for some electronic devices, it is crucial to know how to read the imformation given on the various types of batteries out there.

Let's say we are going to buy a battery for a drone. The given information on the battery is
* 4000mAh
* 30-40c discharge
* 2 cell 7.4V

4000 mAh tells you how much capacity the battery have. The greater the capacity of the battery is, the heavier it become. 

30-40c means that the battery has the ability to provide continuous current at 30 times c. "c" can be thought of as a variable and is calculated as follows

$$\\
\begin{align}
c &= \frac{\text{Capacity of the battery}}{10^3}   \tag{1.1} \\
&= \frac{4000 \, mAh}{1000} = 4A \tag{1.2}
\end{align}
\\$$

This is called the c rating of the battery, it doesn't matter how many cells it has. The c is not dependent on the amount of cells.
Now that we have that number, we can calculate how much current this battery can provide continuously and how much current this battery can provide in burst. Let's calculate that
The continuous capability of this battery to provide current is according to the rating of the battery on the sticker is

$$\\
\begin{align}
30 \cdot c = 30 \cdot 4 = 120A   \tag{1.3} \\
40 \cdot c = 40 \cdot 4 = 160A   \tag{1.3}
\end{align}
\\$$

A small pack like this can provide a 120A - 160A of current continuously until it discharges

