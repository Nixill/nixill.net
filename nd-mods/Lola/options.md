---
layout: page
title: Options - Lola
permalink: /nd-mods/Lola/options
github: https://github.com/Nixill/Synchrony-Lola/
download: https://mod.io/g/crypt/m/lola
downloadTitle: "Lola:"
---

The following options are available to players:

# Presets
Lola comes with two presets that you can select by going to the mod's custom rules and selecting "Use a preset":

## Default Rules
This is Lola's default rules.

## Classic Rules
These rules more closesly resemble the state of the mod when I got my first testing clear:
- Lola does not have chest sight.
- Lola does not have the Package Spell.
- Lola starts with three bombs instead of one.
- Lola cannot pick up shards of broken glass weapons or shovels.
- Lola cannot receive rewards from indirectly-activated shrines.
- Lola cannot receive purchases made at a Conjurer, Transmogrifier, or Pawnbroker.

# Custom Rules
The following custom rules exist:

## Gameplay settings
### Package Spell
This controls whether or not Lola has the Package Spell, with the following options:
- **None:** Lola does not have the Package Spell. *(Default for Classic Rules.)*
- **Replaceable:** Lola starts with the Package Spell, but may replace it with other spells.
- **Innate:** Lola starts with the Package Spell, and cannot lose or replace it. *(Default.)*

### Starting bombs
The number of bombs Lola starts with. May be set to (from left to right) Infinite, 0, 1, 2, 3, 4, or 5. *(Default Rules: 1. Classic Rules: 3.)*

### Chest Vision
If this setting is turned on, Lola is able to innately see the locations of chests, shrines, mimics, shopkeepers, and other item holders at all times, even on the map. However, their contents remain obscured. *(Default Rules: On. Classic Rules: Off.)*

### Allow picking up Glass Shards
If this setting is turned on, Lola is able to pick up the shards of glass weapons and shovels that they were holding before they broke. Only the Lola that was actually holding the Glass item may pick up the Shard. *(Default Rules: On. Classic Rules: Off.)*

### Receive shrine rewards
Lola may activate Sacrifice, Pain, Fireball, and Feast Shrines without Dying. (This is always true, regardless of the value of this setting.)

If this setting is turned on, Lola will receive the rewards from activating those shrines as part of their normal stair item collection. *(Default Rules: On. Classic Rules: Off.)*

### Receive tile purchases
If this setting is turned on, Lola will receive items spawned by Conjurer and Transmogrifier transaction tiles, or the Pawnbroker's Trade Offers or Special Offers, as part of their normal stair item collection. *(Default Rules: On. Classic Rules: Off.)*

### Bounce on attempted violation
*(Added in 1.4.0. Pre-1.4.0 gameplay treats this option as false.)*

If this setting is turned on, moves that would cause Lola to attempt to pick up an item or use a shrine are ignored, rather than killing them. It will instead act like the player idled for a turn, usually dropping groove chain. *(Defaults to Off in both rulesets.)*

### Automatically claim Package interactions
*(Added in 1.4.0. Pre-1.4.0 gameplay treats this option as false.)*

If this setting is turned on, a package summoned by Lola with Package Spell and then immediately opened by environmental damage will be claimed by the Lola that summoned it. If off, the contents will be unclaimed. *(Default Rules: On. Classic Rules: Off [no effect anyway].)*

## Multiplayer settings
These settings may only be changed in a multiplayer server. They have no effect in singleplayer.

### Death unclaims items
If this setting is turned on, Lola does not receive items if they left the floor by dying. *(Default Rules: Off. CLassic Rules: On.)*

## Silly settings
These are a couple sillier settings.

### Greater Package enemies
If on, when Lola uses Greater Package Spell facing an enemy, that enemy will be crated. This can unlock stairs if it's a miniboss or boss. However, it doesn't despawn the boss's adds! *(Default Rules: On. Classic Rules: Off.)*

### Lute mode
As my favorite vanilla character is Melody, enabling this rule changes Lola to a Golden Lute user, allowing a combination of Melody and Lola gameplay. *(Defaults to Off in both rulesets.)*

# Options
The following user options have no effect on gameplay, just on rendering or score tracking:

## Outline colors
You can modify the outline colors used by the mod for item highlights.
- **Safe items:** Items that Lola may safely pick up (Potion, Golden Lute, dropped items, dropped shards). Defaults to #2b42b4.
- **Claimed items:** Items that the current Lola has claimed for the end of the floor. Defaults to #42b42b.
- **Other players' claimed items:** Items that a different Lola has claimed for the end of the floor. Defaults to #969696.
- **Chance items:** Items that the current Lola has claimed for the end of the floor, but will only receive one. Defaults to #b49d2b.
- **Dangerous items:** Items that Lola has not claimed. Deadly on pickup. Defaults to #b42b42.
- **Dangerous shrines:** Shrines that will kill Lola on contact. Defaults to #b42b42.

## View Lola changelog
Should be self-explanatory - opens the [changelogs](changelogs.md).

## Best Times (Lola)
Allows viewing your personal records with the mod! There's also an option to disable saving times.

## Show guide
Shows a small in-game help guide to the user.

## Show guide in pause menu
If this setting is on, a "Guide to Lola" option appears in the pause menu. It can be turned off here.