---
title: Temperature and Weather
description: Rain rain, go away, come again another day.
published: true
date: 2023-06-02T06:17:33.267Z
tags: 
editor: markdown
dateCreated: 2023-05-29T15:20:56.790Z
---

# Temperature
Fundementally the server calculates a temperature for every block coordinate in the game. This impacts loads of other mechanics, such as crop viability and weather. But is not in of itself a visible mechanic.

---
### Notes for development
Conductivity of 1 is true superconductor and 0 is true insulator. Neither is realistic.

UpwardBias is currently 35%, might need to be 100%, play around and test it.

Decay tends towards 0f from either direction. Lava is 100f, ice is -10f, but f is relative. Decay rate is 0.95, so every time a block ticks, i multiply a block by .95, which is a really long decay time. Might need shorter.

Might have to increase average value on decay, (avg something) which will increase time to heat up but neds to be balanced. Might need to decay more aggressive and make the spread delta more agressive, and set the temp values higher to account for the slow ramp up.

Every block has a conductivity value, and some blocks have a base temperature, so those blocks spread their temp through the system

line 21 of ThermalWorld defines how it ticks the simulation. It will only tick around players on the server for up to 9 chunks around them, and has a hard limit on the amout of the tick it takes, currently 20% of the tick (10ms)


Visualize with a color particle on block tick to see how the temperature is actually moving. Might be smart to do a quick computation, like when a player places a block, run the temp system, instead of waiting on the random ticker to hit it. 

Whole system is focused on being basically right, but as efficently and fast as possible, not as accuratley as possible. 

If its too hot, set the player on fire, if its too cold, slowly freeze the player. Set it so direct sunlight can thaw them enough to move. 

Sunlight just halves the players temp so no matter how cold it is, it helps them.

Add thermal resistance to mobs and armor types.

Bears can handle cold, so you approach a bear on the frozen mountain and freeze while it just coes up and beats the shit out of you