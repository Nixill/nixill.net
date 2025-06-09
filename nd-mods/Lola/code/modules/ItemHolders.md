---
layout: page
title: ItemHolders - Lola
permalink: /nd-mods/Lola/code/modules/ItemHolders
github: https://github.com/Nixill/Synchrony-Lola/
download: https://mod.io/g/crypt/m/lola
downloadTitle: "Lola:"
---

`local ItemHolders = require "Lola.mod.ItemHolders"`

Functions on this page interface with the `Lola_holders` component, marking or checking items as safe to be picked up by previous holders or anyone.

- [`ItemHolders.add(holder, item)`](#itemholdersaddholder-item)
- [`ItemHolders.addPID(playerPID, item)`](#itemholdersaddpidplayerpid-item)
- [`ItemHolders.check(item, player)`](#itemholderscheckitem-player)
- [`ItemHolders.checkAllPIDs(item, playerIDs)`](#itemholderscheckallpidsitem-playerids)
- [`ItemHolders.checkPID(item, player)`](#itemholderscheckpiditem-player)
- [`ItemHolders.copy(fromItem, toItem)`](#itemholderscopyfromitem-toitem)
- [`ItemHolders.reset(item)`](#itemholdersresetitem)


# `ItemHolders.add(holder, item)`
Adds a player to an item's holder list. If the item is already marked as held by that player, nothing changes.
 
- `holder` (entity table or entity id): The player to add to the holder list.
- `item` (entity table or entity id): The item to which the player should be added.

Returns `true` if the player was added to the list or `false` if they were already on it. If any parameters are invalid, `nil` is returned.

To pass `holder` as a player ID, use `addPID()` instead.


# `ItemHolders.addPID(playerPID, item)`
Adds a player to an item's holder list. If the item is already marked as held by that player, nothing changes.

- `playerPID` (player id): The player to add to the holder list.
- `item` (entity table or entity id): The item to which the player should be added.

Returns `true` if the player was added to the list or `false` if they were already on it. If any parameters are invalid, `nil` is returned.

To pass `holder` as an entity, use `add()` instead.


# `ItemHolders.check(item, player)`
Checks whether an item was held by a specific player.

- `item` (entity table or entity id): The item that should be checked.
- `player` (entity table or entity id): The player that should be checked for.

Returns `true` if that item was held by that player, or the item is `safe`. Returns `false` otherwise. If any parameters are invalid, `nil` is returned.

To pass `player` as a player ID, use `checkPID()` instead.


# `ItemHolders.checkAllPIDs(item, playerIDs)`
Checks whether an item was held by any of the players.

- `item` (entity table or entity id): The item that should be checked.
- `playerIDs` (table mapping player id -> true): The player IDs to check.

Returns `true` if that item was held by any player in the set, or the item is `safe`. Returns `false` otherwise. 


# `ItemHolders.checkPID(item, player)`
Checks whether an item was held by a specific player.

- `item` (entity table or entity id): The item that should be checked.
- `player` (player id): The player that should be checked for.

Returns `true` if that item was held by that player, or the item is `safe`. Returns `false` otherwise. If any parameters are invalid, `nil` is returned.

To pass `player` as an entity, use `check()` instead.


# `ItemHolders.copy(fromItem, toItem)`
Copies the list of holders from one item to another.

- `fromItem` (entity table or entity id): The item whose holder list should be copied.
- `toItem` (entity table or entity id): The item whose holder list should be overwritten.

Returns `true` if the list was successfully copied, and `nil` if any parameter was invalid. Never returns `false`.


# `ItemHolders.reset(item)`
Removes all holders from the item - except its current holder, if any.

- `item` (entity table or entity id): The item from which all holders should be removed.

Returns the previous list of holders. If any parameters are invalid, `nil` is returned.
