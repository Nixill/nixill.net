---
layout: page
title: RevealedItems - Lola
permalink: /nd-mods/Lola/code/modules/RevealedItems
github: https://github.com/Nixill/Synchrony-Lola/
download: https://mod.io/g/crypt/m/lola
downloadTitle: "Lola:"
---

`local RevealedItems = require "Lola.mod.RevealedItems"`

Functions on this page interface with the `Lola_revealedBy` and `Lola_descentCollectItems` components to track items that will be collected on the stairs.

- [`check(item)`](#revealeditemscheckitem)
- [`getRevealedItems(player)`](#revealeditemsgetrevealeditemsplayer)
- [`getRevealedItemsPID(playerPID)`](#revealeditemsgetrevealeditemspidplayerpid)
- [`mark(revealer, item)`](#revealeditemsmarkrevealer-item)
- [`markPID(revealerPID, item)`](#revealeditemsmarkpidrevealerpid-item)
- [`unmark(item)`](#revealeditemsunmarkitem)
- [`unmarkAll(player)`](#revealeditemsunmarkallplayer)
- [`unmarkAllPID(playerID)`](#revealeditemsunmarkallpidplayerid)


# `RevealedItems.check(item)`
Checks the reveal state of an item.

- `item` (entity table or id): The item to be checked for marks.

Returns `false` if the item is unclaimed, otherwise the PID of the player that has claimed it. `nil` is returned if the call fails.


# `RevealedItems.getRevealedItems(player)`
Returns a table of all items a player has marked as revealed.

- `player` (entity table or id): The player whose claimed items to retrieve.

Returns a list of entity tables that the player has claimed, in order of claim.


# `RevealedItems.getRevealedItemsPID(playerPID)`
Returns a table of all items a player has marked as revealed.

- `playerPID` (entity table or id): The player whose claimed items to retrieve.

Returns a list of entity tables that the player has claimed, in order of claim.


# `RevealedItems.mark(revealer, item)`
Marks an item as revealed by a specific player. If this item is already marked as revealed by another player, it will be removed from that player's list before being added to the end of the new player's list (even if those are the same player).

- `revealer` (entity table or id): The player to be marked as the item's revealer.
- `item` (entity table or id): The item to be marked as revealed.

Returns the player ID of the player that had previously claimed the item, or 0 if it was unclaimed. Returns `nil` if the call fails.


# `RevealedItems.markPID(revealerPID, item)`
Marks an item as revealed by a specific player. If this item is already marked as revealed by another player, it will be removed from that player's list before being added to the end of the new player's list (even if those are the same player).

- `revealerPID` (player id): The player to be marked as the item's revealer.
- `item` (entity table or id): The item to be marked as revealed.

Returns the player ID of the player that had previously claimed the item, or 0 if it was unclaimed. Returns `nil` if the call fails.


# `RevealedItems.unmark(item)`
Marks an item as not revealed. If it was revealed by a player, it is also removed from that player's list (if they have one).

- `item` (entity table or id): The item to be unmarked.

Returns the player ID of the player that had previously claimed the item, or 0 if it was unclaimed. Returns `nil` if the call fails.


# `RevealedItems.unmarkAll(player)`
Unclaims all items a player had claimed.

- `player` (entity table or id): The player whose items should be unclaimed.

Returns `nil`.


# `RevealedItems.unmarkAllPID(playerID)`
Unclaims all items a player had claimed.

- `playerID` (player id): The player whose items should be unclaimed.

Returns `nil`.