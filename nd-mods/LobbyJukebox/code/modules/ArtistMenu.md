---
layout: page
title: ArtistMenu - Lobby Jukebox
permalink: /nd-mods/LobbyJukebox/code/modules/ArtistMenu
---

`local ArtistMenu = require "LobbyJukebox.menu.ArtistMenu"`

# `ArtistMenu.getAvailableArtists()`
Gets a list of all artists that are currently available to select.

Returns a list of `Soundtrack.Artist` enum keys for available artists.

# `ArtistMenu.getName(key)`
Gets the name of an artist. Only works for vanilla artists.

- `key`: The `Soundtrack.Artist` enum key.

# `ArtistMenu.pickArtist()`
Selects a random available artist.

Returns:
1. The `Soundtrack.Artist` enum value of a random available artist.
2. The `Soundtrack.Artist` enum key of the same artist.
