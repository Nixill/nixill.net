---
layout: page
title: Variants - Lobby Jukebox
permalink: /nd-mods/LobbyJukebox/code/modules/Variants
---

`local Variants = require "LobbyJukebox.info.Variants"`

Tracks that deal with selecting variants for the various songs.

# `Variants.finallyPlay(track)`
Plays the given track.

- `track` ([`MusicControl.MusicParams`](MusicControl.md#class-musicparams)): The track for which to get available artists.
  - `type`, `mod`, `artistKey`, `bossKey`, `zoneKey`, `floor`, `vocalsKey`, `variant`, and `playLayers` must be specified, where applicable.

# `Variants.getArtistsFor(track)`
- `track` ([`MusicControl.MusicParams`](MusicControl.md#class-musicparams)): The track for which to get available artists.
  - `type`, `mod`, `bossKey`, `zoneKey`, `floor` must be specified, where applicable.

Returns a list of strings representing the `Soundtrack.Artist` enum keys for which music exists for a track.

# `Variants.getLayersFor(track)`
- `track` ([`MusicControl.MusicParams`](MusicControl.md#class-musicparams)): The track for which to get available artists.
  - `type`, `mod`, `artistKey`, `bossKey`, `zoneKey`, `floor` must be specified, where applicable.

Returns a list of objects with the following information:
- `id` (string): The `Soundtrack.LayerType` enum value.
- `name` (string): The human-readable name of the layer.

# `Variants.getVariantsFor(track)`
- `track` ([`MusicControl.MusicParams`](MusicControl.md#class-musicparams)): The track for which to get available variants.
  - `type`, `mod`, `artistKey`, `bossKey`, `zoneKey`, `floor` must be specified, where applicable.

Returns a list of objects with the following information:
- `id` (string): The `Soundtrack.Variant` enum value.
- `name` (string): The human-readable name of the variant.

# `Variants.getVocalistsFor(track)`
- `track` ([`MusicControl.MusicParams`](MusicControl.md#class-musicparams)): The track for which to get available vocalists.
  - `type`, `mod`, `artistKey`, `bossKey`, `zoneKey`, `floor` must be specified, where applicable.

Returns a list of strings representing the `Soundtrack.Vocals` enum keys for which shopkeepers exist for a track.

# `Variants.hasMultipleVariants(track)`
- `track`:([`MusicControl.MusicParams`](MusicControl.md#class-musicparams)): The track for which to determine the existence of variants.
  - `type`, `mod`, `bossKey`, `zoneKey`, `floor` must be specified, where applicable.

Returns `true` if the given song has more than one possible variant, whether that be in artists, shopkeepers, layers, or actual named variants.

# `Variants.openArtistDropdown(track)`
Opens a dropdown to select an artist for a given track.

Once an option is selected, `openVocalistDropdown()` is called on the same track.

If only one artist is available for the given track, this dropdown is skipped and `openVocalistDropdown()` is called immediately.

- `track` ([`MusicControl.MusicParams`](MusicControl.md#class-musicparams)): The track for which to get available artists.
  - `type`, `mod`, `bossKey`, `zoneKey`, `floor` must be specified, where applicable.

# `Variants.openLayersDropdown(track)`
Opens a dropdown to select layers for a given track.

This menu stays open until "Play" is selected. Once that happens, `finallyPlay()` is called on the track.

If the track is only one layer, this dropdown is skipped and `finallyPlay()` is called immediately.

- `track` ([`MusicControl.MusicParams`](MusicControl.md#class-musicparams)): The track for which to get available artists.
  - `type`, `mod`, `artistKey`, `bossKey`, `zoneKey`, `floor`, `vocalsKey`, `variant` must be specified, where applicable.

# `Variants.openVariantDropdown(track)`
Opens a dropdown to select a variant for a given track.

Once an option is selected, `openLayersDropdown()` is called on the same track.

If no variant is available for the given track, this dropdown is skipped and `openLayersDropdown()` is called immediately.

- `track` ([`MusicControl.MusicParams`](MusicControl.md#class-musicparams)): The track for which to get available artists.
  - `type`, `mod`, `artistKey`, `bossKey`, `zoneKey`, `floor`, `vocalsKey` must be specified, where applicable.

# `Variants.openVocalistDropdown(track)`
Opens a dropdown to select a vocalist for a given track.

Once an option is selected, `openVariantDropdown()` is called on the same track.

If no vocalist is available for the given track, this dropdown is skipped and `openVariantDropdown()` is called immediately.

- `track` ([`MusicControl.MusicParams`](MusicControl.md#class-musicparams)): The track for which to get available artists.
  - `type`, `mod`, `artistKey`, `bossKey`, `zoneKey`, `floor` must be specified, where applicable.
