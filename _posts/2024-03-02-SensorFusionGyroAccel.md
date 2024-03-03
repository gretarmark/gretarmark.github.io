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

## Software implementation

* Start by initializing register addresses and variables as in figure 4.
* Make a void function to initialize the MPU6050 IMU sensor as in figure 5.
* Make a void function to read the accelerometer values as in figure 6.
* Make a void function to read the gyroscope values as in figure 7.
* Set up the while loop and run the void functions you made as show in figure 8.

![Fig 4]({{ site.baseurl }}/images/SensorFusionUSB/Initialize_variables_fig1.png "zero order"){:width=20%}  
**Figure 4: Initialize register addresses and variables for MPU6050.**

![Fig 5]({{ site.baseurl }}/images/SensorFusionUSB/Void_function_init_MPU6050.png "zero order"){:width=20%}  
**Figure 5: Void function used to initialize the MPU6050 IMU sensor.**

![Fig 6]({{ site.baseurl }}/images/SensorFusionUSB/Void_function_readAccel_MPU6050.png "zero order"){:width=20%}  
**Figure 6: Void function used to read the acceleration values from the MPU6050 IMU sensor.**

![Fig 7]({{ site.baseurl }}/images/SensorFusionUSB/Void_function_readGyro_MPU6050.png "zero order"){:width=20%}  
**Figure 7: Void function used to read the gyroscope values from the MPU6050 IMU sensor.**

![Fig 8]({{ site.baseurl }}/images/SensorFusionUSB/While_MPU6050.png "zero order"){:width=20%}  
**Figure 8: The main loop.**

#### References

[1] USB communication STM32. YouTube. Hamed. [Link](https://www.youtube.com/watch?v=ihIRUtQR18E)

