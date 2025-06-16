---
layout: page
title: Code - Lola
permalink: /nd-mods/Lola/code/events
---

Lola registers the following event handlers (all handler names except overrides are prefixed with `Lola_`):

| Event                         | Handler name                     | Filter                                          | Order                     | Sequence | Module                          |
| :---------------------------- | :------------------------------- | :---------------------------------------------- | :------------------------ | :------- | :------------------------------ |
| `animateObjects`              | `partialDirectionalSpriteChange` |                                                 | `directionalSpriteChange` | 1        | `Lola.event.Animations`         |
| `entitySchemaLoadEntity`      | `addComponents`                  |                                                 | `overrides`               | 1        | `Lola.event.Entity`             |
| `entitySchemaLoadNamedEntity` | `settings`                       | `Lola_Lola`                                     |                           |          | `Lola.event.Entity`             |
| `inventoryAddItem`            | `untrack`                        |                                                 | `unmap`                   | 1        | `Lola.event.Inventory`          |
| `itemConsume`                 | `glassShard`                     |                                                 | `convert`                 | 1        | `Lola.event.Inventory`          |
| `levelLoad`                   | `heldItemsSafe`                  |                                                 | `initialItems`            | 1        | `Lola.event.Level`              |
| `menu`                        | `bestTimes`                      | `Lola_bestTimes`                                |                           |          | `Lola.BestTimes`                |
| `menu`                        | `guide`                          | `Lola_guide`                                    |                           |          | `Lola.event.menu.Guide`         |
| `menu`                        | override `pause`                 |                                                 |                           | 1        | `Lola.event.menu.Guide`         |
| `menu`                        | `pbDetails`                      | `Lola_pbDetails`                                |                           |          | `Lola.BestTimes`                |
| `objectDeath`                 | `dontCollectOnDeath`             | `Lola_descentCollectItems`                      | `dead`                    | 1        | `Lola.event.Object`             |
| `objectDeath`                 | `deathCollectItems`              | `controllable`                                  | `descent`                 | 1        | `Lola.event.Object`             |
| `objectDescentEnd`            | `descent`                        | `controllable`                                  | `collectItems`            | 1        | `Lola.event.Object`             |
| `objectFacing`                | `updateFacing`                   | `Lola_partialDirectionalSpriteChange`, `sprite` | `sprite`                  | 1        | `Lola.event.Object`             |
| `objectInteract`              | `shrineDeath`                    | `interactableNegateLowPercent`                  | `lowPercent`              | 1        | `Lola.event.Object`             |
| `objectInteract`              | `chestRevealer`                  | `storage`, `interactableSelfDestruct`           | `selfDestruct`            | -1       | `Lola.event.Object`             |
| `objectSpawn`                 | `shrineDetected`                 | `Lola_revealedBy`                               | `overrides`               |          | `Lola.event.Shrine`             |
| `objectSpawn`                 | `transactionItems`               | `Lola_revealedBy`                               | `overrides`               |          | `Lola.event.TransactionHandler` |
| `objectTakeDamage`            | `crateAttacker`                  | `Lola_interactedBy`                             | `armorMinimumDamage`      | -1       | `Lola.event.Object`             |
| `objectTryCollectItem`        | `itemDeath`                      | `Lola_forcedLowPercent`                         | `lowPercent`              | -1       | `Lola.event.Object`             |
| `render`                      | `outlineClaimedItems`            |                                                 | `outlines`                | 1        | `Lola.event.Render`             |
| `runComplete`                 | `unlockLolaAchievement`          |                                                 | `leaderboardSubmission`   | 1        | `Lola.compat.Achievements`      |
| `settingsPresetSave`          | `addVersionNumbers`              |                                                 | `mods`                    | 10       | `Lola.event.settingsPresetSave` |
| `shopkeeperTransaction`       | `setTransaction`                 | `transactionSpawnItem`                          | `spawnItem`               | -1       | `Lola.event.TransactionHandler` |
| `shopkeeperTransaction`       | `setTransaction`                 | `transactionSellItem`                           | `spawnItem`               | -1       | `Lola.event.TransactionHandler` |
| `shopkeeperTransaction`       | `clearTransaction`               | `transactionSpawnItem`                          | `spawnItem`               | 1        | `Lola.event.TransactionHandler` |
| `shopkeeperTransaction`       | `clearTransaction`               | `transactionSellItem`                           | `spawnItem`               | 1        | `Lola.event.TransactionHandler` |
| `shrine`                      | overide `sacrifice`              |                                                 |                           | 1        | `Lola.event.Shrine`             |
| `shrine`                      | overide `pain`                   |                                                 |                           | 1        | `Lola.event.Shrine`             |
| `shrine`                      | overide `Sync_feast`             |                                                 |                           | 1        | `Lola.event.Shrine`             |
| `shrine`                      | overide `Sync_fire`              |                                                 |                           | 1        | `Lola.event.Shrine`             |
| `spellcast`                   | `crateItem`                      | `Lola_spellcastPackageItems`                    | `convertItems`            | 1        | `Lola.event.Spellcast`          |
| `spellcast`                   | `chestItem`                      | `Lola_spellcastPackageItemsGreater`             | `convertItems`            | 2        | `Lola.event.Spellcast`          |
| `storageDetach`               | `itemTracker`                    |                                                 | `item`                    | 1        | `Lola.event.Inventory`          |
| `NecroEdit_spawn`             | `spawnSafe`                      | `Lola_holders`                                  | `attributes`              | 1        | `Lola.event.NecroEdit`          |
