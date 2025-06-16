---
layout: page
title: Events - LobbyJukebox
permalink: /nd-mods/LobbyJukebox/code/events
---

LobbyJukebox registers the following event handlers (all handler names except overrides are prefixed with `LobbyJukebox_`):

| Event                     | Handler name                                          | Filter                                 | Order                | Sequence | Module                             |
| :------------------------ | :---------------------------------------------------- | :------------------------------------- | :------------------- | :------- | :--------------------------------- |
| `levelLoad`               | `spawnJukebox`                                        |                                        | `lobbyLevel`         | 1        | `LobbyJukebox.entity.Jukebox`      |
| `objectInteract`          | `openJukeboxMenu`                                     | `LobbyJukebox_interactableOpenJukebox` | `configInteractable` | 1        | `LobbyJukebox.entity.Jukebox`      |
| `levelLoad`               | `queueDifferentTrack`                                 |                                        | `music`              | -1       | `LobbyJukebox.event.Level`         |
| `musicPlay`               | `lobbyMusicAutoplay`                                  |                                        | `playAudio`          | 1        | `LobbyJukebox.event.Music`         |
| `musicLayersUpdateVolume` | override `applyTileProximityVolumeModifiers`          |                                        |                      | 1        | `LobbyJukebox.event.Music`         |
| `musicLayersUpdateVolume` | override `MageZone_applyItemProximityVolumeModifiers` |                                        |                      | 1        | `LobbyJukebox.event.Music`         |
| `musicLayersUpdateVolume` | override `applyEntityProximityVolumeModifiers`        |                                        |                      | 1        | `LobbyJukebox.event.Music`         |
| `contentLoad`             | `mergeArtists`                                        |                                        | `snapshots`          | 1        | `LobbyJukebox.menu.ArtistMenu`     |
| `menu`                    | `artistMenu`                                          | `LobbyJukebox_artistMenu`              |                      |          | `LobbyJukebox.menu.ArtistMenu`     |
| `menu`                    | `nowPlaying`                                          | `LobbyJukebox_nowPlaying`              |                      |          | `LobbyJukebox.menu.NowPlaying`     |
| `menu`                    | `playlist`                                            | `LobbyJukebox_playlist`                |                      |          | `LobbyJukebox.menu.Playlist`       |
| `menu`                    | override `settings`                                   |                                        |                      | 1        | `LobbyJukebox.menu.Settings`       |
| `contentLoad`             | `mergeShopkeepers`                                    |                                        | `snapshots`          | 1        | `LobbyJukebox.menu.ShopkeeperMenu` |
| `menu`                    | `shopkeeperMenu`                                      | `LobbyJukebox_shopkeeperMenu`          |                      |          | `LobbyJukebox.menu.ShopkeeperMenu` |
