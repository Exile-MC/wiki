---
title: Temperature and Weather
description: Rain rain, go away, come again another day.
published: true
date: 2023-06-02T06:04:14.951Z
tags: 
editor: markdown
dateCreated: 2023-05-29T15:20:56.790Z
---

# Temperature
Fundementally the server calculates a temperature for every block coordinate in the game. This impacts loads of other mechanics, such as crop viability and weather. But is not in of itself a visible mechanic.

---
### Notes for development
Conductivity of 1 is true superconductor and 0 is true insulator. Neithr is realistic.

UpwardBias is currently 35%, might need to be 100%, play around and test it.

Decay tends towards 0f from either direction. Lava is 100f, ice is -10f, but f is relative. 

Every block has a conductivity value, and some blocks have a base temperature, so those blocks spread their temp through the system

line 21 of ThermalWorld defines how it ticks the simulation. It will only tick around players on the server for up to 9 chunks around them, and has a hard limit on the amout of the tick it takes, currently 20% of the tick (10ms)