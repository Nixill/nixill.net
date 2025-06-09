---
layout: page
title: Components - Lola
permalink: /nd-mods/Lola/code/components
github: https://github.com/Nixill/Synchrony-Lola/
download: https://mod.io/g/crypt/m/lola
downloadTitle: "Lola:"
---

This is the list of components that Lola registers.


# `Lola_descentCollectItems`
A carrier of this component will receive any items they reveal upon using the stairs to leave the floor.

The `revealedItems` field should be modified using the [`RevealedItems`](modules/RevealedItems.md) module, rather than directly.

- `active` (bool): Whether or not collection is actually active. Default `true`.
- `randomizer` (entity ID): Randomizer entity to be used to pick items from single-choice groups.
- `revealedItems` (list of int): A list of the IDs of items that were revealed on the current floor, in order. Default `{}`.

This component is given to `Lola_Lola`.


# `Lola_forcedLowPercent`
A carrier of this component will instantly die if they pick up any items or use any directly-usable shrines.

The `mod.Lola.gameplay.bounce` setting being true will cause such moves to be ignored instead.

- `active` (bool): If `false`, these checks are skipped. Default `true`.
- `killerName` (const translatable string): What should be "Killed by:" if this component activates. Default `"Lola's Curse"`.
- `allowedItems` (set of string): A set (string = true) of the entity types that the character may pick up. Default `{}`.

This component is given to `Lola_Lola` as:
```lua
Lola_forcedLowPercent = {
  allowedItems = {
    MiscPotion = true
  } 
}
```


# `Lola_holders`
An item with this component will not kill a `Lola_forcedLowPercent` entity if their player ID is part of the `playerIDs` table, or `safe` is true.

At the start of each floor, the list of `playerIDs` is reset to only the current holder.

- `playerIDs` (set of player ID): A set of the player IDs that have held the item. Default `{}`.
- `safe` (bool): If true, any player may pick up the item.

This component is given to any entity with `itemNegateLowPercent`.


# `Lola_interactedBy`
If an entity with this component is attacked or interacted with by a player, that player's ID is stored here.

If such an entity is then opened or killed and drops one or more items with `Lola_revealedBy`, those items get the same player ID in that component as contained by this one.

- `playerID` (player id): The player ID that last interacted with this entity. Default 0.

This component is given to any entity with `storage`.


# `Lola_partialDirectionalSpriteChange`
Adds to this entity's spritesheet's `frameX` depending on facing direction, while allowing some directions to not cause that value to change from its most recent value.

- `frameX` (const table(Action.Direction → int)): Maps a direction to the frameX offset. Default `{}`.
- `ignored` (const set of Action.Direction): Specifies which facing directions should not change the `lastFacing` field. Default `{}`.
- `lastFacing` (Action.Direction): The last non-ignored direction this entity was facing.


# `Lola_revealedBy`
An item with this component will be received by the player with the specified ID at the end of the floor, if that player has `Lola_descentCollectItems`.

Its field should be set using the [`RevealedItems`](modules/RevealedItems.md) module, rather than directly.

- `playerID` (player id): The player ID that will receive this item. Default 0.

This component is given to any entity with `itemNegateLowPercent`.


# `Lola_spellcastFlyawayPackage`
A spellcast with this component creates a flyaway which varies based on the targets of that spell.

- `baseText` (const translatable string): The text normally used for the spellcast flyaway.
- `cantAfford` (const translatable string): The text used for the spellcast flyaway when an item isn't packaged because it's unaffordable.
- `enemyCrate` (const translatable string): The text used for the spellcast flyaway when an enemy is packaged. *(Currently unused because of a bug.)*
- `noTargets` (const translatable string): The text used for the spellcast flyaway when an empty package is created.
- `offsetY` (const int): The number of pixels by which to offset the flyaway.


# `Lola_spellcastPackageItems`
A spellcast with this component causes an adjacent item to be replaced with a crate containing that item.

It is given to `Lola_SpellcastPackage`.


# `Lola_spellcastPackageItemsGreater`
A spellcast with this component causes an adjacent item to be replaced with a chest containing that item, or (if a setting is turned on) an adjacent enemy to be replaced with a crate containing that enemy.

It is given to `Lola_SpellcastPackageGreater`.


