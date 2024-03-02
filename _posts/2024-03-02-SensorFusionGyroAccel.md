---
layout: post
title: Gyroscope & Accelerometer sensor fusion - STM32 
published: true
---

To maintain balance in the air, Unmanned Aerial Vehicles (UAVs) like drones rely on sensor fusion. This process combines data from multiple sensors, including gyroscopes and accelerometers, to create a comprehensive understanding of the environment.

## USB communication using STM32 and MPU6050

To begin with, it's a good step to setup the IMU sensor and do some experiments on its measurements.

* D- (D minus): is part of the "voltage signal differential pair" in the USB communication protocol. In STMCubeIDE this is called "USB_OTG_FS_DM".
* D+ (D plus): is also part of the "voltage signal differential pair" in the USB communication protocol. In STMCubeIDE this is called "USB_OTG_FS_DP".
  * The reason for using two signals D- and D+ is to reduce noise in the USB communications.
  * If the signal changes from 0 to 1 and from 1 to 0 in each clock tick, this means 0 in USB binary.
  * If the signal does not change in each clock tick, it means 1 in USB binary.     

![Fig 1]({{ site.baseurl }}/images/SensorFusionUSB/USB_fig1.png "zero order"){:width=20%}  
**Figure 1: USB data transfer, [Link](https://electronics.stackexchange.com/questions/407131/why-does-usb-only-use-2-lines-for-rx-tx-instead-of-multiple-data-lines).**

#### References

[1] USB communication STM32. YouTube. Hamed. [Link](https://www.youtube.com/watch?v=ihIRUtQR18E)

