---
layout: page
title: Code - Lola
permalink: /mods/Lola/code/events
github: https://github.com/Nixill/Synchrony-Lola/
download: https://mod.io/g/crypt/m/lola
downloadTitle: "Lola:"
---

Lola registers the following event handlers (all handler names except overrides are prefixed with `Lola_`):

| Event                         | Handler name                     | Filter                                          | Order                     | Sequence | Description                                                                                   |
| :---------------------------- | :------------------------------- | :---------------------------------------------- | :------------------------ | :------- | :-------------------------------------------------------------------------------------------- |
| `animateObject`               | `partialDirectionalSpriteChange` |                                                 | `directionalSpriteChange` | 1        | Enables Lola to have different sprites depending on facing direction.                         |
| `entitySchemaLoadEntity`      | `addComponents`                  |                                                 | `overrides`               | 1        | Adds Lola components to other entities.                                                       |
| `entitySchemaLoadNamedEntity` | `settings`                       | `Lola_Lola`                                     |                           |          | Adds settings-based components to the Lola entity.                                            |
| `inventoryAddItem`            | `untrack`                        |                                                 | `unmap`                   | 1        | When an item is added to an inventory, unmark it as revealed and untrack it from shown items. |
| `itemConsume`                 | `glassShard`                     |                                                 | `convert`                 | 1        | When a glass shard is dropped, if the setting is enabled, mark it as held by that player.     |
| `levelLoad`                   | `heldItemsSafe`                  |                                                 | `initialItems`            | 1        | Mark all items as only held by their current holder.                                          |
| `menu`                        | override `pause`                 |                                                 |                           | 1        | If a setting is enabled, add "Guide to Lola" to the pause menu.                               |
| `menu`                        | `guide`                          |                                                 |                           |          | Displays a small help guide for Lola.                                                         |
| `objectDeath`                 | `dontCollectOnDeath`             | `Lola_descentCollectItems`                      | `dead`                    | 1        | If a setting is enabled, unclaim all items on death.                                          |
| `objectDeath`                 | `deathCollectItems`              | `controllable`                                  | `descent`                 | 1        | If all players descended, collect items as appropriate.                                       |
| `objectDescentEnd`            | `descent`                        | `controllable`                                  | `collectItems`            | 1        | If not stairs, no collecting items. Also, when all players are descended, collect all items.  |
| `objectFacing`                | `updateFacing`                   | `Lola_partialDirectionalSpriteChange`, `sprite` | `sprite`                  | 1        | Update Lola's facing direction, but only in approved directions.                              |
| `objectInteract`              | `shrineDeath`                    | `interactableNegateLowPercent`                  | `lowPercent`              | 1        | Shrine interactions are forbidden.                                                            |
| `objectInteract`              | `chestRevealer`                  | `storage`, `interactableSelfDestruct`           | `selfDestruct`            | -1       | Mark chests as revealed by their opener.                                                      |
| `objectSpawn`                 | `shrineDetected`                 | `Lola_revealedBy`                               | `overrides`               |          | If a setting is enabled, items from shrines are claimed.                                      |
| `objectSpawn`                 | `transactionItems`               | `Lola_revealedBy`                               | `overrides`               |          | If a setting is enabled, items from transaction tiles are claimed.                            |
| `objectTakeDamage`            | `crateAttacker`                  | `Lola_interactedBy`                             | `armorMinimumDamage`      | -1       | Mark crates as interacted by their attacker.                                                  |
| `objectTryCollectItem`        | `itemDeath`                      | `Lola_forcedLowPercent`                         | `lowPercent`              | -1       | Item pickups are forbidden.                                                                   |
| `render`                      | `outlineClaimedItems`            |                                                 | `outlines`                | 1        | Add outlines to items when focused on a Lola.                                                 |
| `settingsPresetSave`          | `addVersionNumbers`              |                                                 | `mods`                    | 10       | Add Lola's mod version number to settings exports.                                            |
| `shopkeeperTransaction`       | `setTransaction`                 | `transactionSpawnItem`                          | `spawnItem`               | -1       | Set a conjurer or transmog transaction to the current player.                                 |
| `shopkeeperTransaction`       | `setTransaction`                 | `transactionSellItem`                           | `spawnItem`               | -1       | Set a pawnbroker transaction to the current player.                                           |
| `shopkeeperTransaction`       | `clearTransaction`               | `transactionSpawnItem`                          | `spawnItem`               | 1        | Clear a conjurer or transmog transaction.                                                     |
| `shopkeeperTransaction`       | `clearTransaction`               | `transactionSellItem`                           | `spawnItem`               | 1        | Clear a pawnbroker transaction.                                                               |
| `shrine`                      | overide `sacrifice`              |                                                 |                           | 1        | Items spawned from Shrine of Sacrifice should be claimed by whoever triggered them.           |
| `shrine`                      | overide `pain`                   |                                                 |                           | 1        | Items spawned from Shrine of Pain should be claimed by whoever triggered them.                |
| `shrine`                      | overide `Sync_feast`             |                                                 |                           | 1        | Items spawned from Shrine of the Feast should be claimed by whoever triggered them.           |
| `shrine`                      | overide `Sync_fire`              |                                                 |                           | 1        | Items spawned from Shrine of Fire should be claimed by whoever triggered them.                |
| `spellcast`                   | `crateItem`                      | `Lola_spellcastPackageItems`                    | `convertItems`            | 1        | Package a nearby item on use of Package Spell.                                                |
| `spellcast`                   | `chestItem`                      | `Lola_spellcastPackageItemsGreater`             | `convertItems`            | 2        | Package a nearby item or enemy on use of Greater Package Spell.                               |
| `storageDetach`               | `itemTracker`                    |                                                 | `item`                    | 1        | When an item is revealed, mark it as revealed and shown.                                      |
| `NecroEdit_spawn`             | `spawnSafe`                      | `Lola_holders`                                  | `attributes`              | 1        | Items spawned from NecroEdit should be marked as safe immediately.                            |
