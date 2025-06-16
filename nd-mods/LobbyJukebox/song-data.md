---
layout: page
title: Song Data - Lobby Jukebox
description: "Contribute song data to Lobby Jukebox"
permalink: /nd-mods/LobbyJukebox/song-data
---

As of now, the only way for LobbyJukebox to properly support a mod's song titles and artists is to contribute the data directly. Support for `GameSong.Type` enum data, or for mods and resource packs to define their own music title parameters locally, is planned for a future version!

# Add the data to my mod!
When contributing data for a mod's songs directly to LobbyJukebox via a pull request, you'll be dealing with two modules:

- [`LobbyJukebox.info.SongTitleTable`](#the-songtitletable)
- [`LobbyJukebox.info.Variants`](#the-variants-module)

The SongTitleTable is simply a big lua table of all the information known about every song's titles and artists.

## The SongTitleTable
To understand what to add, I first need to go over the concept of a "track key". A track key is composed of, separated by spaces:
- The [`Soundtrack.TrackType`](https://vortexbuffer.com/synchrony/docs/modules/necro.game.data.Soundtrack/#enum-TrackType) enum *value* for the track, though `credits` and `main_menu` aren't used.
- For a boss track, the [`Boss.Type`](https://vortexbuffer.com/synchrony/docs/modules/necro.game.level.Boss/#enum-Type) enum *key* for the track.
- For a zone track, the [`LevelSequence.Zone`](https://vortexbuffer.com/synchrony/docs/modules/necro.game.level.LevelSequence/#enum-Zone) enum *key* for the track, then a space, then the floor number.
- Where necessary, the [`Soundtrack.Variant`](https://vortexbuffer.com/synchrony/docs/modules/necro.game.data.Soundtrack/#enum-Variant) enum *value* for the track.

This results in constructions like
- "`lobby`"
- "`boss FORTISSIMOLE`"
- "`zone MageZone_MAGE_ZONE 2`"
- "`boss DEATH_METAL `" - Note that this string ends with a space! The FamilyJules version of the Death Metal song has variants `"a"` and `""`, where the empty string is used to denote the default variant and "a" the polka variant.

For boss and zone keys, the enum *key* is used for the boss or zone selection, rather than *value*, because the value is dependant on what mods are loaded. If three mods all add an extra zone as "zone 6", which one does the track key `zone 6 2` mean?

Therefore, enum keys are used instead. The enum key is `(mod's namespace)_(first argument passed to the extend function)`, such as `MageZone_MAGE_ZONE`.

Once you have the track key, use it to add a song title to `titles._default` to set the track's title for all artists.

If the track's title changes on a per-artist basis (for example, different selected soundtracks produce different mixes), then you'll also add that title key under the correct artist enum key to override it.

To set the artist's name, go to `artists._trackOverrides`, add the track key there, and set the artist.

As a somewhat complete example (though with existing data omitted):

```lua
return {
  titles = {
    _default = {
      ["zone TheAstros_SPACE_ZONE 1"] = "Ready for Launch",
      ["zone TheAstros_SPACE_ZONE 2"] = "Interplanetary Ascent",
      ["zone TheAstros_SPACE_ZONE 3"] = "Spilled Starlight",
      ["boss TheAstros_BLACK_HOLE"] = "Oblivion"
    },
    GIRLFRIEND_RECORDS = {
      ["zone TheAstros_SPACE_ZONE 1"] = "Blast Offbeats",
      ["zone TheAstros_SPACE_ZONE 2"] = "Galactic Groove",
      ["zone TheAstros_SPACE_ZONE 3"] = "Falling Starrs",
      ["boss TheAstros_BLACK_HOLE"] = "Infinity"
    }
  },
  artists = {
    _trackOverrides = {
      ["zone TheAstros_SPACE_ZONE 1"] = "TwistBit",
      ["zone TheAstros_SPACE_ZONE 2"] = "TwistBit",
      ["zone TheAstros_SPACE_ZONE 3"] = "TwistBit",
      ["boss TheAstros_BLACK_HOLE"] = "TwistBit"
    }
  }
}
```

## The Variants module
Mod music is assumed to just have a single variant that plays across any artist, with no shopkeeper tracks.. If your music doesn't violate this assumption, then you don't need to touch the Variants module. Otherwise, you may need to modify the following functions.

It's worth noting that here the `track` parameter of the methods isn't the same as a "track key" above. Instead, it's a table that contains the following values:

- `type`: The `Soundtrack.TrackType` value
- `mod`: The mod the song's boss or zone is from, if applicable. `""` otherwise.
- `zoneKey`: The `LevelSequence.Zone` key of the zone, if applicable.
- `floor`: The floor within the zone, if applicable.
- `bossKey`: The `Boss.Type` key of the boss, if applicable.
- `artistKey`: The `Soundtrack.Artist` key of the soundtrack, if applicable. (Not set in `getArtistsFor()` or `hasMultipleVariants()`.)

- `hasMultipleVariants(track)`: Returns `true` if the track has more than a single variant.
- `getArtistsFor(track)`: Returns a list of all the artist keys that are valid for a given track.
- `getVocalistsFor(track)`: Returns a list of all the shopkeeper (vocalist) keys that are valid for a given track and artist.
- `getVariantsFor(track)`: Returns a list of all the variant keys that are valid for a given track and artist.
- `getLayersFor(track)`: Returns a list of ID/name combinations for all layers in a song.

You can read the existing functions for examples of how it should work. If you need help modifying this file accurately, you can request help in the Pull Request; I'll be happy to help!

# Define it yourself!
Neither of these are supported yet. I'm going to work on adding them, though!

Once they're implemented, the priority order for getting information will be:
- If the song is played from a resource pack, `LobbyJukebox.json` in that resource pack.
- `SongTitleTable.lua` and `Variants.lua`.
- If the song is played from a lua mod, `LobbyJukebox.json` in that mod.
- `GameSong` module.

## The `GameSong` module
I didn't know about the GameSong module! A future LobbyJukebox update will support reading it, though it won't be as fully-featured as modifying my files directly or using a `LobbyJukebox.json` (no variant support, for example).

## `LobbyJukebox.json` in the mod
This was a relatively recent feature request, and I want to implement it because it would also be possible to include in resource packs. I'm still working on deciding the exact format, so check-back later!