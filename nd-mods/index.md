---
layout: page
title: Mods for NecroDancer
description: I make mods for Crypt of the NecroDancer!
permalink: /nd-mods/
---

I make mods for [Crypt of the NecroDancer](https://store.steampowered.com/app/247080/Crypt_of_the_NecroDancer/)! On this page you can see some of what I've done.

*(Note: NecroDancer's [SYNCHRONY DLC](https://store.steampowered.com/app/2094810/Crypt_of_the_NecroDancer_SYNCHRONY/?snr=1_5_9__405) is required to play mods.)*


# Content mods
These mods add new gameplay content or mechanics! Most players will probably be interested in these.

## Health Times Floor
Health Times Floor is a simple mod that just multiplies every enemy's base health by the current floor.

I made it when [Infinite Slot Capacity](https://mod.io/g/crypt/m/infiniteslotcapacity) was first released, to give myself a bigger challenge against it.

The latest mod version on PC is **1.0.0**. It is not yet approved on consoles.

- [More info](HTF/index.md)
- [Subscribe on mod.io](https://mod.io/g/crypt/m/htf)
- [Source code and bug tracker](https://github.com/Nixill/Synchrony-HTF)

## How Batty!
How Batty! is a simple mod that changes every enemy's AI to bat.

I just figured I could. :)

The latest mod version on PC is **1.0.0**. It is not yet approved on consoles.

- [More info](HowBatty/index.md)
- [Subscribe on mod.io](https://mod.io/g/crypt/m/howbatty)
- [Source code and bug tracker](https://github.com/Nixill/Synchrony-HowBatty)

## LobbyJukebox
LobbyJukebox is a mod that adds a jukebox to the lobby to play the game's music.

This one, I made because I wanted to have background music for mod-coding streams that isn't just "the game's lobby music on eternal loop", but that automatically switches to game music when I start playing to test.

It has also been used to provide background music to competitive necrodancer events.

The current version is **1.0.3**. There is no version approved for consoles.

- [More info](LobbyJukebox/index.md)
- [Subscribe on mod.io](https://mod.io/g/crypt/m/lobbyjukebox)
- [Source code and bug tracker](https://github.com/Nixill/Synchrony-LobbyJukebox)

## Lola
Lola is a character who can't directly pick up items, but has to open chests and leave the items sitting on the floor to receive them.

This is my most complete mod, a fun character idea I'd had when I thought "What if we had a character forced to play low%?".

As of the latest website update, the latest mod version on PC is **1.4.2**, and the latest mod version on consoles is **1.3.1**.

[WinnerBit](https://bsky.app/profile/twistbit.cc) did the artwork for this mod!

Version **1.3.1** of this mod was featured in Week 39 of the Weekly Challenge.

- [More info](Lola/index.md)
- [Subscribe on mod.io](https://mod.io/g/crypt/m/lola)
- [Source code and bug tracker](https://github.com/Nixill/Synchrony-Lola)

## No Health Limits
No Health Limits is a mod that removes all characters' health limits (it removes the `healthLimit` component from all entities).

The current version on PC is **1.0.1**. There is no version approved for consoles.

- [Subscribe on mod.io](https://mod.io/g/crypt/m/nohealthlimits)

Source code:
```lua
local Event = require "necro.event.Event"

Event.entitySchemaLoadEntity.add("logComponents", { order = "itemBans", sequence = 1 }, function(ev)
  ev.entity.healthLimit = nil
end)
```

## Save Editor
Save Editor can be used to modify singleplayer single-zones and lobby progression.

The current version on PC is **1.1.1**. There is no version approved for consoles.

- [More info](SaveEditor/index.md)
- [Subscribe on mod.io](https://mod.io/g/crypt/m/saveeditor)
- [Source code and bug tracker](https://github.com/Nixill/Synchrony-SaveEditor)

## Spatial Distortions
Spatial Distortions randomizes the order of the floors in a run.

The current version on PC is **0.0.5**. There is no version approved for consoles.

- [More info](SpatialDistortions/index.md)
- [Subscribe on mod.io](https://mod.io/g/crypt/m/spatialdistortions)
- [Source code and bug tracker](https://github.com/Nixill/Synchrony-SpatialDistortions)

## Switcheroo
Switcheroo randomly changes every item of yours every floor.

It's my first mod, dating back to when Synchrony was just a fan-made unofficial client.

- [More info](./Switcheroo)
- [Subscribe on mod.io](https://mod.io/g/crypt/m/switcheroo)
- [Source code and bug tracker](https://github.com/Nixill/Synchrony-Switcheroo)


# Library mods
These mods add functions that other mods can use. Most players will probably barely know these are here, but other developers may be interested in them.

## NixLib
NixLib is simply a library of functions and minor components that I don't want to keep redefining in every mod I make.

<!-- - [More info](./NixLib) -->
- More info: Coming soon
- [View on mod.io](https://mod.io/g/crypt/m/nixlib)
- [Source code and bug tracker](https://github.com/Nixill/Synchrony-NixLib)

## Power Settings
Power Settings is a library mod that overhauls Synchrony's own Settings API to add additional features and settings types.

<!-- - [More info](./PowerSettings) -->
- More info: Coming soon
- [View on mod.io](https://mod.io/g/crypt/m/powersettings)
- [Source code and bug tracker](https://github.com/Nixill/Synchrony-PowerSettings)