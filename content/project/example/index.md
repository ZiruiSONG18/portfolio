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
2.