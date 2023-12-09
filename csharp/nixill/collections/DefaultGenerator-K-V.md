---
layout: page
title: DefaultGenerator\<K, V\> class (Nixill.Collections)
permalink: /csharp/nixill/collections/DefaultGenerator-K-V
---

A `Generator<K, V>` that always returns the type's default.

# Type parameters
- `K` - The type of keys in the dictionary
- `V` - The type of values in the dictionary

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
`V` - Returns the default of the value's type.

Parameters:
- `K` **`key`** - This parameter is ignored.

Returns: `default(V)`.