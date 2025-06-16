---
layout: page
title: ShopkeeperMeun - Lobby Jukebox
permalink: /nd-mods/LobbyJukebox/code/modules/ShopkeeperMeun
---

`local ShopkeeperMenu = require "LobbyJukebox.menu.ShopkeeperMenu"`

# `ShopkeeperMenu.getAvailableVocalists()`
Returns a list of all `Soundtrack.Vocals` enum keys corresponding to available vocalists.

# `ShopkeeperMenu.pickShopkeeper()`
Picks a random vocalist from the game's available vocalists.

Returns:
1. The `Soundtrack.Vocals` enum value of a random available vocalist.
2. The key of the same enum entry.
