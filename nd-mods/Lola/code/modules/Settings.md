---
layout: page
title: Settings - Lola
permalink: /nd-mods/Lola/code/modules/Settings
---

`local LoSettings = require "Lola.Settings"`

# `LoSettings.get(node, ...)`
Returns the current value of the given settings node, prefixing the given key with `"mod.Lola."`. See the [Settings list](../settings.md) for more information.

💡 Do not prefix your keys with `mod.Lola.` yourself. For example, to get the value of the `mod.Lola.silly.luteMode` setting, use `LoSettings.get("silly.luteMode")`.