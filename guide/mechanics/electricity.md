---
title: Electricity
description: This ones complicated
published: true
date: 2023-06-15T04:41:48.462Z
tags: 
editor: markdown
dateCreated: 2023-05-29T15:16:58.040Z
---

# Electric Power
Electricity is an important component of running processing, defenses, and more within your terreitories.


## Energy Networks
In order to run machines, users build a local energy network, that consists of three types of blocks.
- Generation Blocks, Like Solar panels wind turbines, fuel burning generators, geothermal systems etc.
- Consumption Blocks, being the machines players want to use and need to power, such as electric furnaces, crushers, refineries, etc.
- Storage blocks, which store generated energy that goes unused by the network.

In order to power a block, the player places a generation block, and ensures its operating propeerly. When the requirements for the block are met it generates a certain number of units of energy per tick based on its condition, fuel source, parameters, etc. 

The player then places the block they want to power, and use a wiring tool to connect it to the power source. When in use, every consumption block has a specific required amount of energy units in order to run. As long as at least that much energy is generated on the network every tick, the machine will operate as intended.

Excess power simply disapates unless a storage block exists on the network, which will collect it, and be drawn from when other power is not available.

## Technical
Each generation block produces x units per tick, however, the system only runs the calculation to determine how much power is generated once every 20 ticks, and does so with all values 20x. This saves server tick, and generates way less garbage, but the server will still display values as if it were per tick to the player, an update just wont occur more then once a second (20 ticks) to those values.

Wiring doesnt matter as long as every block on the network is wired together. If wiring becomes to complicated, the wiring tool can be used to disconnect all wires from one block, or remove all wires in the network for rewiring. Wires do not cost anything to place, and are merely virtual visulization of what blocks are registered in a system. Wires are rendered as particle lines, only when the player is holding the wiring tool.

When a new block is wired to the existing network, the server stores that block based on its type in the network list of connected blocks. The system always calculates the following in this order:
- All generation blocks on the network calculate how much they generate that second
- All consumption blocks subtract their needed amount for that 20 tick period until either:
  - The system runs out of energy, in which case any remaining consumption blocks become unpowered. When this occurs, the system will check if there is any available power in storage blocks in the network and use that before moving onto the next step.
  - All consumption blocks in the network are powered, and any remaining energy dissapates
- Unless a storage block exists on the network, then remaining power goes there.


Un sorted notes for development
- Virtual wires, run calculations only once every 20 ticks, but do it at 20x, and display everything to the player as if it were per tick.
- Dont register wires, let the wires determine the order in which producers and consumers operate, and then just run through the list in order for each connected system. way more efficient, way less garbage generated