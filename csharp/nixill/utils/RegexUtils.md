---
layout: page
title: RegexUtils class (Nixill.Utils)
permalink: /csharp/nixill/utils/RegexUtils
---

Utilities and extension methods for working with Regex.

`public static class RegexUtils`

# Static methods
## `TryMatch(string, string, out Match)`
`bool` - Returns whether or not a match was successful, while also assigning the match.

Parameters:
- `string` **`input`** - The input to test against the regex.
- `string` **`pattern`** - The pattern against which input should be tested.
- `out Match` **`match`** - When the method exits, this contains the `Match` object formed by the other two arguments (even if this method returns `false`).

Returns: Whether or not `match` was successful.

# Extension methods
## `Regex.TryMatch(string, out Match)`
`bool` - Returns whether or not a match was successful, while also assigning the match.

Parameters:
- `this Regex` **`regex`** - The regex to test matches against.
- `string` **`input`** - The input to test against the regex.
- `out Match` **`match`** - When the method exits, this contains the `Match` object formed by the other two arguments (even if this method returns `false`).

Returns: Whether or not `match` was successful.

## `Match.TryGroup(int, out string)`
`bool` - Returns whether or not a group was successful, while also assigning the value.

Parameters:
- `this Match` **`match`** - The match to pull groups from.
- `int` **`number`** - Which group should be pulled.
- `out string` **`value`** - When the method returns `true`, this contains the group's value. If the method returned `false`, this contains nothing.

Returns: Whether or not the group was successful.

## `Match.TryGroup(string, out string)`
`bool` - Returns whether or not a group was successful, while also assigning the value.

Parameters:
- `this Match` **`match`** - The match to pull groups from.
- `string` **`name`** - Which group should be pulled.
- `out string` **`value`** - When the method returns `true`, this contains the group's value. If the method returned `false`, this contains nothing.

Returns: Whether or not the group was successful.
