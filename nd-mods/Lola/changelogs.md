---
layout: page
title: Changelogs - Lola
permalink: /nd-mods/Lola/changelogs
github: https://github.com/Nixill/Synchrony-Lola/
download: https://mod.io/g/crypt/m/lola
downloadTitle: "Lola:"
---

Changelogs are listed in order of most to least recent versions.

# Version 1.4:
## 1.4.0.1
*(Version 1.4.0.1 was released June 4, 2025.)*

Removed extraneous `print()` statements leftover from debugging.

## 1.4.0
*(Version 1.4.0 was released June 4, 2025.)*

### Changes
- Added option to bounce off items/shrines instead of dying to them.
  - This still drops the player's Groove Chain, though this effect is prevented by Ballet Shoes.
  - Coins or safe items beneath unsafe items cannot be collected.
  - This option is not enabled by Default Rules or Classic Rules. It must be turned on manually.
- Added hints when interacting with shrines or items.
  - These hints are displayed whether the bounce option is enabled or disabled.

### Package Spell changes
For lola to claim an item from a crate, either they must be the one to open it, or they must be the last player to interact with it before non-player damage opens it.

Previously, creating a crate via Package Spell did not count as "interacting" with it, which would mean that Packaging an item and then getting a Red Dragon or Goblin Bomber to open it (without touching it in between) would not grant Lola the item.

This has been changed. Creating a crate via Package Spell now counts as an interaction. In the above scenarios, Lola now claims the item.

An option has been added to reverse this behavior. Classic Rules uses this option, though that has no effect because Classic Rules also disables Package Spell entirely.

### RuleCheck changes
The following changes have been made to rule-checking (for best times and IGA) specifically:

- No Beat Mode is now tracked. IGA can be earned with or without No Beat Mode, while the Best Times menu has a separate list of entries for No Beat Mode.
- Weekly Challenge Mode can now earn in-game achievements or set best times, though this has no effect on Week 39 as it's using an older version of the mod.
- Default Rules requires that the "Automatically claim package interactions" setting be true (which it is by default).
- Classic Rules no longer checks the "Greater PAckage enemies" rule. Since the Package Spell is disabled, this rule has no effect.

### Modding changes
- Added function `RevealedItems.check(item)`.

# Version 1.3:
## 1.3.1
*(Version 1.3.1 was released December 3rd, 2024.)*

**This is the latest approved version on consoles, and the version that the 39th Weekly Challenge uses.**

Added a small guide, accessible from either the pause menu or the mod's options menu. The pause menu entry can also be disabled in the mod's options menu.

## 1.3.0
*(Version 1.3.0 was released March 22nd, 2024.)*

### Changes
- Added a red outline to items that Lola has not claimed (but can) and cannot pick up.
- Added a red outline to shrines that Lola cannot bump.
- Added options to change these and all outline colors.
- Pawnbroker Trade Offers and Special Offers are now automatically claimed by Lola under Default Rules. They will not be charged to pick one up.
  - This can be changed with the "Receive tile purchases" setting.
- Added a tracker of best times, viewable in the options.

### Modding changes
- Added module `Lola.mod.RuleCheck`.

# Version 1.2:
## 1.2.4
*(Version 1.2.4 was released October 23rd, 2023.)*

Fixed a bug with saving settings presets.

## 1.2.3
*(Version 1.2.3 was released October 8th, 2023.)*

Removed dependencies on NixLib and PowerSettings.

### Modding changes
Added module `Lola.mod.ShownItems`.

## 1.2.2
*(Version 1.2.2 was released August 7th, 2023.)*

- Fixed a potential future crash if IGA is not enabled.
- Don't assume all `storage` has `Lola_interactedBy`; filter on the latter instead.

## 1.2.1
*(Version 1.2.1 was released July 21st, 2023.)*

Fixed item rejection markings on conjurer/transmog when IGA is enabled.

## 1.2.0
*(Version 1.2.0 was released July 20th, 2023.)*

### Gameplay changes

#### Achievements!
Support has been added for the InGameAchievements mod with three achievements to be earned:
- **Lola the Lucky:** Clear a run with Default Rules.
- **Lola the Persistent:** Clear a run with Classic Rules.
- **Lola the Adaptible:** Clear a run with either Default Rules or Classic Rules, but do not destroy or skip collecting any claimed items.

If you already earned the achievement "Lola: Hardcore!", it'll translate into "Lola the Lucky" and you don't need to unlock it again.

For Classic Rules, pause the game and go to "Customize", "Custom rules", accept the popup if one appears, "Mod options", "Lola", "Use a preset", and finally "Classic Rules".

To earn achievements, you must play singleplayer; the custom rules must match one of the presets in "Use a preset"; they must not change during the run, and Dancepad, Phasing, and No Beat modes must be disabled.

*(As of version 1.4.0, No Beat Mode is allowed. However, it was not allowed as of 1.2.0.)*

#### Other gameplay changes
Under Default Rules:
- Greater Package will now capture enemies.
  - This includes minibosses and bosses; have fun!
- Dying in multiplayer will now cause players to miss item claiming.

These are both settings that can be toggled. In both cases, the opposite behavior is true in Classic Rules.

### Aesthetic changes
- When a player will miss items as a result of dying or exiting by a trapdoor, the highlight on those items is removed to signal to other players that nobody will be getting those items.
- Lola's Bestiary artwork has been signed by its artist, WinnerBit! Also, the focus has been moved so that partial shots (such as the multiplayer mid-run character select screen) look actually at them rather than at a corner of the room.

### Misc changes
- Added changelogs for 1.2.0 and 1.1.x! They're not automatic on update but I may one day add that too.

### Modding/code changes
- Added functions `RevealedItems.unmarkAll(player)` and `RevealedItems.unmarkAllPID(playerID)`.
- The component values `Lola_descentCollectItems.active` and `Lola_forcedLowPercent.active` no longer change every floor.

# Version 1.1:
## 1.1.5
*(Version 1.1.5 was released July 10th, 2023.)*

Items are no longer outlined when placed by Level Editor.

## 1.1.4
*(Version 1.1.4 was released July 10th, 2023.)*

Lola can now safely pick up items spawned from the in-game editor!

*Modder note:* This version adds the component field `Lola_holders.safe`.

## 1.1.3
*(Version 1.1.3 was released July 8th, 2023.)*

WinnerBit made some lovely artwork for the Bestiary, viewed when selecting Lola as a character. The previous artwork, simply a very enlarged sprite, has thus been removed.

I updated my mod translation template, and part of that action was to add a translation key for the word "Infinite" as senn in the number-of-bombs option.

## 1.1.2
*(Version 1.1.2 was released July 4th, 2023.)*

Some shortcuts I'd taken in the item pickup code meant that any "choose one of these three" groups you'd claimed would always be granted after guaranteed items revealed later - the order matters if they're part of the same slot. Also, holsters weren't recognized until the next floor, when it'd be nice to be able to use it immediately. Both of these have been fixed.

Familiars were previously granted a blue "safe item" outline when that wasn't necessary. That's been fixed too.

## 1.1.1
*(Version 1.1.1 was released July 4th, 2023.)*

Previously, you'd still be charged the price for items from a shop even if the shopkeeper is missing or dead. This update addressed that so you can now get those items for free.