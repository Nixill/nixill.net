---
layout: page
title: ToStringGenerator\<K\> class (Nixill.Collections)
permalink: /csharp/nixill/collections/ToStringGenerator-K
---

A `Generator<K, string>` that always returns the string representation of the keys.

# Type parameters
- `K` - The type of keys in the dictionary

# Constructors
Only the empty constructor exists.

# Methods
## `CanGenerate(V)`
`bool?` - Always returns `null`.

Parameters:
- `V` **`val`** - This parameter is ignored.

Returns: `null`.

## `CanGenerateFrom(K)`
`bool?` - Always returns `null`.

Parameters:
- `K` **`key`** - This parameter is ignored.

Returns: `null`.

## `Generate(K)`
`int` - Returns the string representation of the supplied value.

Parameters:
- `K` **`key`** - The key for which to generate a hash code.

Returns: `key.ToString()`.