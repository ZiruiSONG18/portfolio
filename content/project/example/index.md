---
slides: example
url_pdf: ""
summary: An example of using the in-built project page.
url_video: ""
date: 2022-02-06T21:10:28.559Z
external_link: ""
url_slides: ""
title: PID-based Robot Car
tags:
  - Deep Learning
links:
  - icon: twitter
    icon_pack: fab
    name: Follow
    url: https://twitter.com/georgecushen
image:
  caption: Photo by rawpixel on Unsplash
  focal_point: Smart
url_code: ""
---
I write a program for this robot car in order that it can move along a straight line. In ideal situation, there is no difference between two wheels, which means that robot car will move along a straight line automatically. But in the reality, the real rotating speeds of two wheels are different due to kinds of factors. So, this robot car cannot move straightly if I simply set two fixed values to two wheels. Thus, a system with feedback control is needed to make sure that the final speeds of two wheels are the same.

1. Design Block Diagram

   The engine motivates two wheels of this robot car so that we need to design a system for the two wheels. Not only do we need two feedback control systems for two wheels respectively, but we also need another system to keep 0 difference between the speed of two wheels.

   The following diagram basically shows the whole project structure.

   ![](1.jpg)
2. Get Fundamental Data

   Since we need a system to help robot car move straightly, we need the original data of the car's movement. 

   The robot car provides a feature that could record how many roations of a wheel in every 0.0025 second. To better represent, I summed every 20 values together as the speed. With the data, I could start up designing my system.

   ```
   fit=stable value*(1-e^(-at) ),where a=1/(when achieve 0.632×stable value)
   ```

   This "fit" means the value we would like to have finally.

   Then we can have a forward transfer function.

   ```
   G(s)=520/44999*(0.588/(s+0.588))
   ```
3. Design PI Controller

   To reduce the steady-state-error, we need to design a PI compensator for this transfer function. Here, frequency response method was used. I plotted the bode diagram of G(s)

   ![](2.jpg)

   After we choose an appropriate 0-dB frequency, we could have:

   ```
   G_C (s)=1333.5 (s+0.901)/s
   ```

   Then, I convert it into z-domain by Tustin method to implement digital system design: 

   ```
   G_CZ (z)=Z{G_C (s)}=(1335z-1332)/(z-1)=D/E
   ```