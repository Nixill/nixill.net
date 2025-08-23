---
layout: page
title: HashCodeGenerator\<K\> class (Nixill.Collections)
permalink: /csharp/nixill/collections/HashCodeGenerator-K
---

A `Generator<K, int>` that always returns the hash code of the keys.

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
`int` - Returns the hash code of the supplied value.

Parameters:
- `K` **`key`** - The key for which to generate a hash code.

Returns: `key.GetHashCode()`.