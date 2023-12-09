---
layout: page
title: CountingGenerator\<K\> class (Nixill.Collections)
permalink: /csharp/nixill/collections/CountingGenerator-K
---

A `Generator<K, int>` that returns an incrementally counted value, starting with zero.

# Type parameters
- `K` - The type of keys in the dictionary

# Constructors
Only the empty constructor exists.

# Properties
## `Count`
`int` - Gets the value that will immediately be returned by the generator (the next integer in sequence).

# Methods
## `CanGenerate(int)`
`bool?` - Returns whether or not a value can be the next returned by the Generator. This is `false` for any value *except* for `Count`.

Parameters:
- `int` **`val`** - The value to check.

Returns: `true` if `val` matches `Count`; `false` otherwise.

## `CanGenerateFrom(K)`
`bool?` - Returns whether or not a value can be generated for the given key without throwing an exception. This is `true` for any key.

Notably, this is `true` even when `key` is `null`, as `Generate(null)` will not throw an exception despite the fact that `null` keys cannot be used in dictionaries.

Parameters:
- `K` **`key`** - This parameter is ignored.

Returns: `true`

## `Generate(K)`
`int` - Returns the next integer in sequence and increments the count.

Parameters:
- `K` **`key`** - This parameter is ignored.

Returns: `Count` (then increments it)