---
title: "DIY 2.4GHz Signal Jammer"
date: 2026-09-30T12:19:00-07:00
draft: false
author: "nosebleeeddd"
tags:
  - DIY
  - Soldering
  - Jammer
image: /images/jammer2.4ghz.jpg
description: "asdad"
toc: true
mathjax: false
---

## Flashing Firmware

This schematic is compatible with the EmenstaV1 Firmware on Github.
Use the web flasher to flash the firmware to ESP32, 

hold down boot to enable flasher.


Disrupts up to 10 meters.

Upgrade NRF24 to E01-ML01DP5 for longer range disruption!

### Build Materials:
```
proto-board x1
ESP32 WROOM-U x1
NRF24L01+PA+LNA x2-4
blue led x1
10uF 50v electrolytic CAP x2
104 ceramic CAP x2
4.7k ohm Resistor x1
0.96 OLED I2C x1
3.7V Li-Ion Battery x1
JST PH 2.0 Connector x1
TP4056 Charging Module (Micro-USB/Type-C) x1
Mini Slide Switch x1
Button x1
PVC Board
M3 Nut/Screw
```

<img src="/images/jammer.jpg" alt="Jammer Pic" style="float: right; margin: 0 0 10px 15px; width: 300px;" /> 

### NOTES:
For the 0.96 Display I bent female header pins to make a socket, 
this way we can disconnect the display for portability

After wiring/soldering everything I used double sided tape to mount the 3.7v to the PVC cutout.

I also used double sided tape for the TP4056 Chargeboard on the back of the protoboard,
that way we can use the JST connector to easily disconnect the lipo and open the device if needed.



