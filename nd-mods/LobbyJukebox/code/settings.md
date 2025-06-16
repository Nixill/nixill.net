---
layout: page
title: Settings - LobbyJukebox
permalink: /nd-mods/LobbyJukebox/code/settings
---

LobbyJukebox contains the following (non-restricted) settings nodes (all nodes prefixed by `mod.LobbyJukebox.`):

# User settings
| Node             | Name                       | Type    | Default value           | Module                             |
| :--------------- | :------------------------- | :------ | :---------------------- | :--------------------------------- |
| `artistMenu`     | Change jukebox soundtracks | Action  |                         | `LobbyJukebox.menu.ArtistMenu`     |
| `artists`        | Artist choices             | Table   | see [below](#artists)   | `LobbyJukebox.menu.ArtistMenu`     |
| `blockedSongs`   | Blocked songs              | Table   | `{}`                    | `LobbyJukebox.mod.MusicControl`    |
| `fadeTime`       | Fade-out time              | Number  | 5                       | `LobbyJukebox.mod.MusicControl`    |
| `loop`           | Loop track                 | Boolean | `false`                 | `LobbyJukebox.mod.MusicTimer`      |
| `seekTime`       | Seek time                  | Number  | 5                       | `LobbyJukebox.mod.MusicControl`    |
| `shopkeeperMenu` | Change jukebox vocalists   | Action  |                         | `LobbyJukebox.menu.ShopkeeperMenu` |
| `shopkeepers`    | Vocalist choices           | Table   | see [below](#vocalists) | `LobbyJukebox.menu.ShopkeeperMenu` |
| `shuffle`        | Shuffle tracks             | Boolean | `true`                  | `LobbyJukebox.mod.MusicControl`    |

## Defaults
### Artists
```lua
{
  A_RIVAL = true,
  CHIPZEL = false,
  DANGANRONPA = false,
  DANNY_B = true,
  FAMILYJULES7X = true,
  GIRLFRIEND_RECORDS = true,
  GROOVE_COASTER = true,
  HATSUNE_MIKU = false,
  OC_REMIX = true,
  VIRT = true,
  _TrackOverrides = {}
}
```

### Vocalists
```lua
{
  MONSTROUS_SHOPKEEPER = false,
  NICOLAS_DAOUST = true,
  NONE = true,
  SHOPKEEPER = true,
  _TrackOverrides = {}  
}
```
