---
title: GeoDrop
description: Just keep mining
published: true
date: 2023-05-30T13:48:55.617Z
tags: 
editor: markdown
dateCreated: 2023-05-29T13:40:28.272Z
---

# GeoDrop
GeoDrop is equivalant in nature to classic civ's "HiddenOre". The servers world is generated with no ore or caves in which to discover it by default. Instead the entire world is stone under the surface. This allows players to have full control of the structures they build underground without anything getting in there way. And since theres no ore in the world, players don't have to worry about cheaters with x-ray getting ahead of them, or having an unfair advantage.

## How it works
Whenever a player mines any block of stone[^1] in the world, the server calculates what to drop based on 3 main factors:
- Y Level: The server only drops items that would already spawn at the y level in which the stone was mined. So a stone block mined at `y=190` will never drop diamond, no matter what.
- Tool Level: There are additional tool levels with specific functionality and additional mechanics to improve the mining experience when customized with skills, but the idea of tool level progression still exists. Each drop has a set tool level that must be used for that drop to have a chance to drop.
- Player Skills: Various skills, perks, and player upgrades will improve mining yield in some fashion, whether giving a chance for additional drops, compacted drops, special item chance, etc.

## Features
This system has a handful of important benefits. 
- Anti X-Ray: This ones pretty simple, since there is no ore in the world, there is no xray.
- Economy and Drop Tuning: Since all drops are based on configuration, they can be adjusted to accomodate for changes in skills, abilities, tool levels, and other mechanics we might add in the future in real time. This also allows us to very carefully fine tune the economy as mining is the entry point for resources in the global system. 
 






[^1]: We chose not to differentiate between pregenerated stone and player placed stone, because the system takes y level into account when determining what to drop. So if a player tries to place a bunch of stone and mine it on the surface, they wont get any good drops. And if they place stone and remine it below ground to get drops, who cares.