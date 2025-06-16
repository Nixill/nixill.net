---
layout: page
title: Lobby Jukebox
permalink: /nd-mods/LobbyJukebox/
---

LobbyJukebox is a mod that plays the game's music in the lobby.

These pages are updated for version **1.0.3** of Lobby Jukebox. There is no approved version on consoles.

To use it, simply load the mod and then reload the lobby. The easiest way to reload the lobby is to use the Quick Restart hotkey, but if that's not bound, you can also enter a monster training and return to the lobby there.

Once you reload the lobby, you should see a jukebox at the northwest corner of the room, and a random song from the game will play. That's all you need to do!

# Controlling your music
To open the music controls, walk up to and bump the Jukebox itself to bring up the Jukebox menu. It looks like this:

{%include image.html url="menu.png" alt="The Lobby Jukebox menu" caption="The Lobby Jukebox menu!" %}

The buttons from left to right are:

1. Restart song
2. Play/pause
3. Fast forward 5 seconds
4. Skip track
5. Shuffle on/off
6. Loop track on/off
7. Playlist
8. Settings

"Loop track" only switches between playing the current track on loop or playing all tracks on loop. There is no "stop playing at end of playlist" mode.

## The Playlist
The playlist lets you control which songs can play in rotation (using the checkboxes), or allow you to play a specific song (using the play button) or a specific variant of a specific song (using the … menu).

The playlist also shows the order in which tracks will be played if shuffle is turned off.

## The Settings
The settings menu lets you change the mod's settings:
- **Shuffle tracks:** When enabled, tracks are played on shuffle. Otherwise, they're played in the order shown in the playlist.
- **Loop track:** When enabled, only one track is played unless manually changed. Otherwise, tracks are played once and then moved on.
- **Change jukebox soundtracks:** Changes which artists can have their songs played through the Jukebox.
- **Change jukebox vocalists:** Changes which shopkeepers can be played atop zone music.

If you have advanced settings enabled, you will also see:
- **Fade-out time:** Songs which cleanly loop will have an artificial fade-out added before transitioning to the next song. The length of this fade-out can be set from 0 to 20 seconds. This has no effect on songs which cleanly end, or on looped music.
- **Seek time:** The fast forward button can have its seek duration changed here, anywhere from 2 to 60 seconds.

# Mod music works too!
If you have a mod such as [Symphony of Sorcery](https://mod.io/g/crypt/m/magezone) or [Devil's Dreaded Darkness](https://mod.io/g/crypt/m/godlightddd) enabled, zone and boss music from that mod can be played in the Jukebox.

# How the code works
- If you want to know more about the various functions the mod has, click [here](code/index.md).
- If you want to contribute song data to the mod, click [here](song-data.md).