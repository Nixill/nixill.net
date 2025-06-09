---
layout: page
title: RuleCheck - Lola
permalink: /nd-mods/Lola/code/modules/RuleCheck
github: https://github.com/Nixill/Synchrony-Lola/
download: https://mod.io/g/crypt/m/lola
downloadTitle: "Lola:"
---

`local RuleCheck = require "Lola.mod.RuleCheck"`

Functions that deal with rules states, for time-tracking and achievement purposes.


# Class `RuleCheck.Result`
A table of the results of a rule check. `nil` is equivalent to `false`.
- `Any` (bool?): If `true`, one of `Default`, `Classic`, or `Lute` is true.
- `Default` (bool?): If `true`, Default Rules were followed.
- `Classic` (bool?): If `true`, Classic Rules were followed.
- `Lute` (bool?): If `true`, Lute Mode Rules were followed.
- `NoRejects` (bool?): If `true`, no items were rejected during the run.
- `Mystery` (bool?): If `true`, Mystery Mode was active during the run.
- `NoBeat` (bool?): If `true`, No Beat Mode was active during the run.


# `RuleCheck.getFollowedRules()`
Returns a `RuleCheck.Result` showing what rules were followed, if any. Only works at the end of a run.