---
layout: page
title: EchoGenerator\<T\> class (Nixill.Collections)
permalink: /csharp/nixill/collections/EchoGenerator-T
---

A `Generator<T, T>` that always returns the same value, which is supplied at construction.

# Type parameters
- `T` - The type of keys *and* values in the dictionary, which must match each other.

# Constructors
Only the empty constructor exists.

# Methods
## `CanGenerate(T)`
`bool?` - Returns whether or not a value can be returned by the Generator. This is `true` for any value.

Notably, this is `true` even when `value` is `null`, as `Generate(null)` will not throw an exception despite the fact that `null` keys cannot be used in dictionaries.

Parameters:
- `T` **`val`** - This parameter is ignored.

Returns: `true`

## `CanGenerateFrom(T)`
`bool?` - Returns whether or not a value can be generated for the given key without throwing an exception. This is `true` for any key.

Notably, this is `true` even when `key` is `null`, as `Generate(null)` will not throw an exception despite the fact that `null` keys cannot be used in dictionaries.

Parameters:
- `T` **`key`** - This parameter is ignored.

Returns: `true`

## `Generate(T)`
`T` - Returns the value specified in the parameter.

Parameters:
- `T` **`key`** - The key for which to generate a value.

Returns: `key`