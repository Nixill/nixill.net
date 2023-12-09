---
layout: page
title: FuncGenerator\<K, V\> class (Nixill.Collections)
permalink: /csharp/nixill/collections/FuncGenerator-K-V
---

A `Generator<K, V>` that runs a function to generate a value.

# Type parameters
- `K` - The type of keys in the dictionary
- `V` - The type of values in the dictionary

# Constructors
There are two constructor overloads:
- `(Func<K, V>)`
- `(Func<K, V>, Func<K, bool?>, Func<V, bool?>)`

Parameters:
- `Func<K, V>` **`func`** - The function used to generate keys.
- `Func<K, bool?>` **`keyCheck`** - The function used to check if keys can be generated from. If not specified, `(key) => null` is used.
- `Func<V, bool?>` **`valCheck`** - The function used to check if values can be generated. If not specified, `(key) => null` is used.

# Properties
## `GeneratingFunc`
`Func<K, V>` - Gets the function used by the generator.

## `KeyCheckFunc`
`Func<K, bool?>` - Gets the key-checking function used by the generator.

## `ValCheckFunc`
`Func<V, bool?>` - Gets the value-checking function used by the generator.

# Methods
## `CanGenerate(V)`
`bool?` - Returns whether or not a value can be returned by the Generator, as determined by `ValCheckFunc`.

Parameters:
- `V` **`val`** - The value to check.

Returns: Determined by `ValCheckFunc`.

## `CanGenerateFrom(K)`
`bool?` - Returns whether or not a value can be generated for the given key without throwing an exception, as determined by `KeyCheckFunc`.

Parameters:
- `K` **`key`** - The key to check.

Returns: Determined by `KeyCheckFunc`.

## `Generate(K)`
`V` - Generates a value for the key, as determined by `GeneratingFunc`.

Parameters:
- `K` **`key`** - The key for which a value should be generated.

Returns: Determined by `GeneratingFunc`.