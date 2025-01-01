---
layout: post
title: Creating Custom Footprints in KiCad 8 for PCB Design
published: false
---

1. Find a datasheet for the item
2. Find the Package Outline chapter showing the dimensions of the item
3. In Kicad, open the footprint editor
4. Click on new footprint
5. Give the footprint a name
6. Now you get the name of the footprint and also the footprint reference
7. If you click on REF you can enter any data you need
  * You can choose what layer is fixed to your footprint
  * You change the reference text. Write the name of the item, e.g. DW01-P
  * Press okay
8. Next choose the grid to be used to lay down the footprint. 
In order to choose the right grid, go back to the datasheet.
Look at the pin spacing/pitch. For DW01-P, it is 0.95mm center to center.
Since there is no 0.95mm grid size, go to edit grids to create a custom spacing.
Leace the origin at x=y=0. 


# USB Power

USB powered circuit boards are typically less than 500mA current consumption.
The USB rail is usually +5VDC, this gives us

$$P = V \cdot I = 5V \cdot 0.5A = 2.5W$$

that we can use at maximum.

## A
