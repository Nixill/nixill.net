---
layout: page
title: SingleValueGenerator\<K, V\> class (Nixill.Collections)
permalink: /csharp/nixill/collections/SingleValueGenerator-K-V
---

A `Generator<K, V>` that always returns the same value, which is supplied at construction.

# Type parameters
- `K` - The type of keys in the dictionary
- `V` - The type of values in the dictionary

# Constructors
There's only one constructor, `(V)`. The `V` is the value to always return.

# Properties
## `Val`
`V` - Gets the value that will always be returned by the generator.

# Methods
## `CanGenerate(V)`
`bool?` - Returns whether or not a value can be returned by the Generator. This is `false` for any value *except* for `Val`.

Parameters:
- `V` **`val`** - The value to check.

Returns: `true` if `val` matches `Val`; `false` otherwise.

## `CanGenerateFrom(K)`
`bool?` - Returns whether or not a value can be generated for the given key without throwing an exception. This is `true` for any key.

Notably, this is `true` even when `key` is `null`, as `Generate(null)` will not throw an exception despite the fact that `null` keys cannot be used in dictionaries.

Parameters:
- `K` **`key`** - This parameter is ignored.

Returns: `true`

## `Generate(K)`
`V` - Returns the initially supplied value.

Parameters:
- `K` **`key`** - This parameter is ignored.

Returns: `Val`