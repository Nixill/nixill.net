---
layout: page
title: Health × Floor
description: "Mod for CotND that multiplies every enemy's health by the current floor"
image: "/img/page/mods/HTF/HTFIcon.png"
permalink: /nd-mods/HTF/
github: https://github.com/Nixill/Synchrony-HTF/
download: https://mod.io/g/crypt/m/htf
downloadTitle: "Health × Floor:"
---

Health × Floor is a mod that multiplies every enemy's base health by the current floor. Good luck!

Enemies that don't normally take knockback have it added if:
- The enemy is knockbackable at all.
- The enemy's normal max health is 1.
- The enemy moves every beat.
- The enemy doesn't have a pattern-based AI (like slimes), a charge (like minotaurs), or a turn delay on changing facing direction (like orcs).

This page is updated for version **1.0.0** of HTF. As of this writing, there is no console-approved version.

# Options
There is one option in the Custom Rules. The "Training health factor" option lets you multiply the enemy's health by a number of your choice on training floors. It also affects the tutorial level. It defaults to 1, and can be set up to 50. And it does not affect any regular gameplay.

# For mod authors
## Module `HTF.HTF`
This module contains nothing. It only exists so that you can use `pcall(require, "HTF.HTF")` to detect if the mod is loaded.

## Event handlers
(Event handlers prefixed with `HTF_`)

| Event                    | Handler name                  | Filter                         | Order         | Sequence | Description                                                    |
| :----------------------- | :---------------------------- | :----------------------------- | :------------ | :------- | :------------------------------------------------------------- |
| `entitySchemaLoadEntity` | `forceKnockback`              |                                | `overrides`   | 1        | For enemies that need it added, forces them to take knockback. |
| `levelLoad`              | `multiplyHealthOnLevelLoad`   |                                | `boss`        | 1        | Multiplies enemy healths at the start of a level.              |
| `objectSpawn`            | `multiplyHealthOnObjectSpawn` | `enemy`, `health`, `spawnable` | `healthBonus` | 1        | multiplies enemy healths when they spawn during a level.       |

## Shared settings
(Node prefixed with `mod.HTF.`)

| Node            | Name                   | Type   | Default value | Module                       |
| :-------------- | :--------------------- | :----- | :------------ | :--------------------------- |
| `trainingFloor` | Training health factor | Number | 1             | `HTF.scripts.MultiplyHealth` |