---
layout: page
title: ShownItems - Lola
permalink: /nd-mods/Lola/code/modules/ShownItems
---

`local ShownItems = require "Lola.mod.ShownItems"`

Tracks items that have been shown and not claimed over the course of a run.


# `ShownItems.collectItem(id)`
Marks an item as collected.

- `id` (entity id): The ID of the item to collect.

Returns `nil`.


# `ShownItems.hasUncollectedItems()`
Returns `ture` if any items are tracked, but not collected. Returns `false` otherwise.


# `ShownItems.trackItem(id)`
Tracks a given item.

- `id` (entity id): The ID of the item to track.

Returns `nil`.


# `ShownItems.untrackItem(id)`
Stops tracking a given item.

- `id` (entity id): The ID of the item to untrack.

Returns `nil`.