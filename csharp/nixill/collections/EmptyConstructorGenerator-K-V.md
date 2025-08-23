---
layout: page
title: EmptyConstructorGenerator\<K, V\> class (Nixill.Collections)
permalink: /csharp/nixill/collections/EmptyConstructorGenerator-K-V
---

A `Generator<K, V>` that always returns a new instance of the value type.

# Type parameters
- `K` - The type of keys in the dictionary
- `V` - The type of values in the dictionary. Must have a parameterless constructor.

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
`V` - Returns a new instance of the value's type.

Parameters:
- `K` **`key`** - This parameter is ignored.

Returns: `new V()`.