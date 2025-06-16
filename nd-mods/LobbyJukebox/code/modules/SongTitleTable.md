---
layout: page
title: SongTitleTable - Lobby Jukebox
permalink: /nd-mods/LobbyJukebox/code/modules/SongInfo
---

`local Info = require "LobbyJukebox.info.SongTitleTable"`

A table containing all the title and artist name information known to Lobby Jukebox.

# Contents:
- [`titles`](#titles-object)
- [`artists`](#artists-object)
- [`vocals`](#vocals-object)

## `titles` object:
- `_default`
- (an [artist key](#what-is-an-artist-key))

The `_default` table maps a [track key](#what-is-a-track-key) to the song's default title.

Each [artist key](#what-is-an-artist-key) table maps a track key to the title of the song played through that artist. This is primarily used for the FamilyJules soundtrack, as he gave every track he covered a different name from Danny B, and for the Danganronpa, Groove Coaster, and Hatsune Miku soundtracks, as those use different songs than the game's regular music entirely.

## `artists` object:
- `_trackOverrides`
- (an [artist key](#what-is-an-artist-key))

The `_trackOverrides` table maps [track keys](#what-is-a-track-key) to the artist that made that track. This is primarily used for mods' music, where the creator of the song doesn't actually match the selected soundtrack's artist (for example, in Mage Zone, the music that plays is made by Creepslime even though the Danny B soundtrack is selected to play from), or for music that always plays Danny B's version of the song even if another soundtrack is selected (story bosses and the training and tutorial musics).

Each [artist key](#what-is-an-artist-key) table contains the following:
- `_default`: The artist's name, used when not overridden by a track.
- `_prefix` and `_suffix`: Appendages to be added to an artist's name, in addition to track-specific information. For example, Girlfriend Records and OC ReMix use `prefix_` for the group, while crediting individual artists at the track level, while Hatsune Miku uses `_suffix` to put "& Hatsune Miku" after each song's artist credit.
- (a [track key](#what-is-a-track-key)): The artist that made the individual track. Uses the `_prefix` and `_suffix`, and overrides even a `_trackOverride`.

## `vocals` object:
Contains just one entry, `_tracks`, which maps [track keys](#what-is-a-track-key) to an object which maps either [artist keys](#what-is-an-artist-key) or `_default` to the name of the performer of vocals for the track.

For shopkeepers in zone music, this is not used, instead going by the names given within the data of the [`Soundtrack.Vocals`](https://vortexbuffer.com/synchrony/docs/modules/necro.game.data.Soundtrack/#enum-Vocals).


# What is a track key?
A track key is, in short, an identifier of track type and location.

It starts with the type of the music, which is either `lobby`, `training`, `tutorial`, `zone`, or `boss` (the [`Soundtrack.TrackType`](https://vortexbuffer.com/synchrony/docs/modules/necro.game.data.Soundtrack/#enum-TrackType) enum values, but without `main_menu` or `credits`). In the case of the first three, that's it.

For `zone`, it's followed by a space, then the enum key of the zone (for example, `ZONE_1` or `MageZone_MAGE_ZONE`), then another space, then the floor number within that zone. For example, `zone ZONE_5 2`. If there are variants, another space precedes the variant letter (for example, `zone ZONE_3 3 h`).

For a boss, the word `boss` is followed by a space, then the enum key of the boss (for example, `boss DEATH_METAL` or `boss MageZone_SYMHPONY_OF_SORCERY`). A variant can also follow in the same way as before, such as in `boss FORTISSIMOLE b`.


# What is an artist key?
An artist key is simply the key of an entry to the [`Soundtrack.Artist`](https://vortexbuffer.com/synchrony/docs/modules/necro.game.data.Soundtrack/#enum-Artist) enum (such as `OC_REMIX` or `DANNY_B`).


# How is information gathered?

## Title
The song's title is in the `titles` key in this table. It's checked as follows:

- If `titles[artistKey]` exists, and `titles[artistKey][trackKey]` exists, then that's the title for the track. (Example: `titles.FAMILYJULES7X["zone ZONE_1 1"] = "Infernal Descent"` overrides `titles._default["zone ZONE_1 1"] = "Disco Descent"`)
- Otherwise, if `titles._default[trackKey]` exists, then that's the title for the track. (Example: `titles._default["boss FRANKENSTEINWAY"] = "Steinway to Heaven"`)
- Otherwise, the track has no title.

Then basic track information is added (such as "Death Metal" or "Zone 1 Floor 1").

## Artist
The song's artist is slightly more complicated, because it can change on both a per-track *and* per-artist basis, and there can be prefixes and suffixes. It's in the `artists` key in the table, and checked as follows:

- If `artists[artistKey]` exists, and `artists[artistKey][trackKey]` exists, then that (with prefix and suffix) is the artist credit. (Example: `artists.HATSUNE_MIKU["zone ZONE_4 1"] = "AlexTrip Sands"`)
- Otherwise, if `artists._trackOverrides[track]` exists, then that's the artist credit. (Example: `artists._trackOverrides["zone MageZone_MAGE_ZONE 2"] = "Creepslime"`)
- Otherwise, if the music comes from a mod, there is no artist credit.
- Otherwise, if `artists[artistKey]` exists, then its `_default` (with prefix and suffix) is the artist credit. (Example: `artists.DANNY_B._default = "Danny Baranowsky"`).

"With prefix and suffix" means that if `artists[artistKey]._prefix` exists, that gets prepended to the artist name (for example, Girlfriend Records puts "Girlfriend Records - " before the individual artists' names), and if `artists[artistKey]._suffix` exists, that gets appended to the artist name (for example, Hatsune Miku adds " & Hatsune Miku" after the individual artists' names). So for example, Miku's zone 4 floor 1 is credited as "AlexTrip Sands & Hatsune Miku".

## Vocals
This is only used for Fortissimole, but it would also work for mod music. `shopkeeperKey` is the enum key of the shopkeeper in use.

- If `vocals._tracks[trackKey]` exists:
  - If `vocals._tracks[trackKey][shopkeeperKey]` exists, use that as the vocalist credit.
  - Otherwise, if `vocals._tracks[trackKey]._default` exists, use that as the vocalist credit. (This is used to credit Mega Ran as Fortissimole.)
- Otherwise, if the current track comes from a mod, do not list a vocalist credit.
- Otherwise, try to get the vocalist's name from the Vocals enum. Use the enum key if that doesn't work.
