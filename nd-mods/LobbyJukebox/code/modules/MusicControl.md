---
layout: page
title: ArtistMenu - Lobby Jukebox
permalink: /nd-mods/LobbyJukebox/code/modules/ArtistMenu
---

`local MusicControl = require "LobbyJukebox.mod.MusicControl"`

# Classes `MusicParams`
A table that may contain the following information:
- `type` (string): The [`Soundtrack.TrackType`](https://vortexbuffer.com/synchrony/docs/modules/necro.game.data.Soundtrack/#enum-TrackType) enum value for the music type.
- `mod` (string?): The mod from which the given song originates (based on its `zoneKey` or `bossKey`).
- `artist` (int?): The [`Soundtrack.Artist`](https://vortexbuffer.com/synchrony/docs/modules/necro.game.data.Soundtrack/#enum-Artist) enum value for the music track. Ignored (by LobbyJukebox) if `artistKey` is specified.
- `artistKey` (string?): The [`Soundtrack.Artist`](https://vortexbuffer.com/synchrony/docs/modules/necro.game.data.Soundtrack/#enum-Artist) enum *key* for the music track.
- `variant` (string?): The [`Soundtrack.Variant`](https://vortexbuffer.com/synchrony/docs/modules/necro.game.data.Soundtrack/#enum-Variant) enum value for the music track, if applicable.
- `playLayers` ([`Soundtrack.LayerType`](https://vortexbuffer.com/synchrony/docs/modules/necro.game.data.Soundtrack/#enum-LayerType) → true): Which layers should be played from the music? If not specified, all of them are except those that by their nature are not played from the variant.

If `type` is `"boss"`:
- `boss` (int?): The [`Boss.Type`](https://vortexbuffer.com/synchrony/docs/modules/necro.game.level.Boss/#enum-Type) enum value for the music track. Ignored (by LobbyJukebox) if `bossKey` is specified.
- `bossKey` (string?): The [`Boss.Type`](https://vortexbuffer.com/synchrony/docs/modules/necro.game.level.Boss/#enum-Type) enum *key* for the music track.

If `type` is `"zone"`:
- `floor` (int?): The floor number for the music track, if it's a "zone" track.
- `vocals` (string?): The [`Soundtrack.Vocals`](https://vortexbuffer.com/synchrony/docs/modules/necro.game.data.Soundtrack/#enum-Vocals) enum value for the music track. Ignored (by LobbyJukebox) if `vocalsKey` is specified.
- `vocalsKey` (string?): The [`Soundtrack.Vocals`](https://vortexbuffer.com/synchrony/docs/modules/necro.game.data.Soundtrack/#enum-Vocals) enum *key* for the music track.
- `zone` (int?): The [`LevelSequence.Zone`](https://vortexbuffer.com/synchrony/docs/modules/necro.game.level.LevelSequence/#enum-Zone) enum value for the music track. Ignored (by LobbyJukebox) if `zoneKey` is specified.
- `zoneKey` (string?): The [`LevelSequence.Zone`](https://vortexbuffer.com/synchrony/docs/modules/necro.game.level.LevelSequence/#enum-Zone) enum *key* for the music track.

# Functions

## `clearQueue()`: nil
Clears the shuffled music queue, forcing it to rebuild when next needed.

## `getNextTrack()`: MusicControl.Params
Returns the next track to play, whether shuffled or sorted, based on the shuffle setting.

## `getNextTrackSequential()`: MusicControl.Params
Gets the next track in sequence (from the currently playing or last-played one).

## `getNextTrackShuffled()`: MusicControl.Params
Returns the next track from the shuffled queue, adding to it afterwards.

## `getSequence()`: list\[MusicControl.Params\]
Gets the sorted music sequence, building it from scratch if not cached.

## `isShuffled()`: boolean
Returns whether or not shuffle is enabled in the user's settings.

## `setShuffled(val)`: nil
Changes whether or not shuffle is enabled.

Params:
- boolean **`val`**: The value to set. If not specified, defaults to the opposite of its current state.

# Settings
## `shuffle`
A boolean setting, defaulting to `true`. Controls whether tracks are played on shuffle or not.
