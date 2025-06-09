---
layout: page
title: Settings - Lola
permalink: /nd-mods/Lola/code/settings
github: https://github.com/Nixill/Synchrony-Lola/
download: https://mod.io/g/crypt/m/lola
downloadTitle: "Lola:"
---

Lola contains the following (non-restricted) settings nodes (all nodes prefixed by `mod.Lola.`):

# User settings
| Node                   | Name                         | Type    | Default value                    | Module                  |
| :--------------------- | :--------------------------- | :------ | :------------------------------- | :---------------------- |
| `changelog`            | View Lola changelog          | Action  |                                  | `Lola.Changelog`        |
| `colors.chance`        | Chance items                 | Color   | `Color.rgba(180, 157, 43, 255)`  | `Lola.event.Render`     |
| `colors.claimed`       | Claimed items                | Color   | `Color.rgba(66, 180, 43, 255)`   | `Lola.event.Render`     |
| `colors.danger`        | Dangerous items              | Color   | `Color.rgba(180, 43, 66, 255)`   | `Lola.event.Render`     |
| `colors.dangerShrine`  | Dangerous shrines            | Color   | `Color.rgba(180, 43, 66, 255)`   | `Lola.event.Render`     |
| `colors.other`         | Other players' claimed items | Color   | `Color.rgba(150, 150, 150, 255)` | `Lola.event.Render`     |
| `colors.safe`          | Safe items                   | Color   | `Color.rgba(43, 66, 180, 255)`   | `Lola.event.Render`     |
| `showGuideInPauseMenu` | Show guide in pause menu     | Boolean | `true`                           | `Lola.event.menu.Guide` |
| `showGuideNow`         | Show guide                   | Action  |                                  | `Lola.event.menu.Guide` |
| `pb.save`              | Save times (Lola)            | Boolean | `true`                           | `Lola.BestTimes`        |
| `pb.view`              | View times (Lola)            | Action  |                                  | `Lola.BestTimes`        |
| `pb.viewNoBeat`        | View no-beat times (Lola)    | Action  |                                  | `Lola.BestTimes`        |

# Shared settings
| Node                     | Name                                     | Type    | Default value                  | Module          |
| :----------------------- | :--------------------------------------- | :------ | :----------------------------- | :-------------- |
| `gameplay.autoInteract`  | Automatically claim package interactions | Boolean | `true`                         | `Lola.Settings` |
| `gameplay.bombs`         | Starting bombs                           | Number  | 1                              | `Lola.Settings` |
| `gameplay.bounce`        | Bounce on attempted violation            | Boolean | `true`                         | `Lola.Settings` |
| `gameplay.glass`         | Allow picking up glass shards            | Boolean | `true`                         | `Lola.Settings` |
| `gameplay.package`       | Package Spell                            | Enum    | `LoEnum.PackageSetting.INNATE` | `Lola.Settings` |
| `gameplay.shrine`        | Receive shrine rewards                   | Boolean | `true`                         | `Lola.Settings` |
| `gameplay.storageVision` | Chest vision                             | Boolean | `true`                         | `Lola.Settings` |
| `gameplay.transaction`   | Receive tile purchases                   | Boolean | `true`                         | `Lola.Settings` |
| `multiplayer.death`      | Death unclaims items                     | Boolean | `false`                        | `Lola.Settings` |
| `preset.classic`         | Classic Rules                            | Action  |                                | `Lola.Settings` |
| `preset.default`         | Default Rules                            | Action  |                                | `Lola.Settings` |
| `preset.easy`            | Easy Mode                                | Action  |                                | `Lola.Settings` |
| `preset.lute`            | Lute Mode                                | Action  |                                | `Lola.Settings` |
| `silly.luteMode`         | Lute mode                                | Boolean | `false`                        | `Lola.Settings` |
| `silly.packageEnemies`   | Greater Package enemies                  | Boolean | `true`                         | `Lola.Settings` |
