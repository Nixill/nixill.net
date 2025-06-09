---
layout: page
title: Settings - Lola
permalink: /nd-mods/Lola/code/modules/Settings
github: https://github.com/Nixill/Synchrony-Lola/
download: https://mod.io/g/crypt/m/lola
downloadTitle: "Lola:"
---

`local LoSettings = require "Lola.Settings"`

# `LoSettings.get(node, ...)`
Returns the current value of the given settings node, prefixing the given key with `"mod.Lola."`. See the [Settings list](../settings.md) for more information.

💡 Do not prefix your keys with `mod.Lola.` yourself. For example, to get the value of the `mod.Lola.silly.luteMode` setting, use `LoSettings.get("silly.luteMode")`.