---
layout: page
title: SongInfo - Lobby Jukebox
permalink: /nd-mods/LobbyJukebox/code/modules/SongInfo
---

`local SongInfo = require "LobbyJukebox.info.SongInfo"`

Functions that deal with song information.

# `getSongInfo(params)`
Gets detailed information on the name, artist, and vocalist of a track.

- `params` ([MusicParams](#class-musicparams)): The parameters of the music track.

Returns a table with:
- `artist` (string?): The artist of the track. `nil` if there is no information.
- `songType` (string): Equal to `params.type`.
- `title` (string?): The title of the track. `nil` if there is no information.
- `titleInfo` (string): The same text as returned by [`getTitleInfo()`](#gettitleinfoparams).
- `vocals` (string?): The singer of the track, if any. `nil` if there is no information.


# `getTitleInfo(params)`
Gets basic information on the context of a track, such as "Zone 3 Floor 1" or "Frankensteinway", that can be used in place of an actual title.

- `params` ([MusicParams](#class-musicparams)): The parameters of the music track.

Returns a string giving that basic title.
