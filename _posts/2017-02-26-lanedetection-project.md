---
layout: post
title:  "Lane Departure Warning System (LDWS)"
date:   2017-02-26
excerpt: "A Lane Detection algorithm can be used in various applications such as; Steering of Autonomous or Semi-Autonomous Vehicles or ADAS systems (e.g. LDWS)."
tag:
- Computer Vision
- Lane Detection
- Autonomous Control
comments: true
project: true
---
Aim of the project is to detect lanes with high accuracy and warn to driver in unintentional lane departures 
(like departure without using signal (blinker)) or wrong lane departures such as crossing over continuous lane borders.
Project is still going on and what you can see in the video is the version of the original one after applied IPM (Inverse Perspective Mapping) in order to obtain lane borders as parallels and original frames on top left. In the video blue circles are indicating lane departures, and the side of the departure (left or right). There is actually a sound which is there to warn driver sychnorous with circles but it is not included in video due to codec issues. In some part of the video (from 1:10 to 3:40), lane borders not obvious or completely covered by asphalt patch (e.g. at 2:29) and it is selected especially to test the system reliability. System works at 83FPS on CPU.

<iframe width="560" height="315" src="//www.youtube.com/embed/4BUzP6X1CHQ" frameborder="0"> </iframe>
