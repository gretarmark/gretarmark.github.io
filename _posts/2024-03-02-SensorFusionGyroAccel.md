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

## Setting up MPU6050 and USB communication in STM32CubeIDE using STM32407G Discovery Board

* Create new project
* Configure all peripherals automatically
* Configure the clocksettings similar to figure 3 below. I choose to have 168MHz.
* Configure the MPU6050 IMU sensor
  * Choose pin PB8 for I2C1 SCL communication to the MPU6050 device as shown in figure 2.
  * Choose pin PB7 for I2C1 SDA communication to the MPU6050 device as shown in figure 2.
  * Go to connectivity and choose I2C in the I2C dropdown menu under GPIO settings.
* Configure the USB communication
  * Go to 

![Fig 2]({{ site.baseurl }}/images/SensorFusionUSB/Configuration_fig1.png "zero order"){:width=20%}  
**Figure 2: Pin configuration for MPU6050.**

![Fig 3]({{ site.baseurl }}/images/SensorFusionUSB/Clockconfig_fig1.png "zero order"){:width=20%}  
**Figure 3: Pin configuration for MPU6050.**

#### References

[1] USB communication STM32. YouTube. Hamed. [Link](https://www.youtube.com/watch?v=ihIRUtQR18E)

