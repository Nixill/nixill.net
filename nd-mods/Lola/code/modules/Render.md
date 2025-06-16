---
layout: page
title: Render - Lola
permalink: /nd-mods/Lola/code/modules/Render
---

`local LoRender = require "Lola.event.Render"`

Functions that return the user settings relating to Lola item outline colors.


# `LoRender.chanceItemColor()`
Returns the color that the user has set to outline single-choice-group claimed items.

This is the value of the `mod.Lola.colors.chance` user-layer setting, which defaults to `Color.rgba(180, 157, 43, 255)`.


# `LoRender.claimedItemColor()`
Returns the color that the user has set to outline claimed items.

This is the value of the `mod.Lola.colors.claimed` user-layer setting, which defaults to `Color.rgba(66, 180, 43, 255)`.


# `LoRender.dangerItemColor()`
Returns the color that the user has set to outline dangerous, unclaimed items.

This is the value of the `mod.Lola.colors.danger` user-layer setting, which defaults to `Color.rgba(180, 43, 66, 255)`.


# `LoRender.dangerShrineColor()`
Returns the color that the user has set to outline dangerous shrines.

This is the value of the `mod.Lola.colors.dangerShrine` setting, which defaults to `Color.rgba(180, 43, 66, 255)`.


# `LoRender.otherClaimedItemColor()`
Returns the color that the user has set to outline other players' claimed items.

This is the value of the `mod.Lola.colors.other` user-layer setting, which defaults to `Color.rgba(150, 150, 150, 255)`.


# `LoRender.safeItemColor()`
Returns the color that the user has set to outline safe items.

This is the value of the `mod.Lola.colors.safe` user-layer setting, which defaults to `Color.rgba(43, 66, 180, 255)`.
