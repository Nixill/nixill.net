---
layout: page
title: Generator\<K, V\> class (Nixill.Collections)
permalink: /csharp/nixill/collections/Generator-K-V
---

A `Generator<K, V>` is used by a `DictionaryGenerator<K, V>` to generate values for keys automatically.

# Derived by

# Methods

## `CanGenerate(V)`
`bool?` - Whether or not a specific value can be generated immediately.

More specifically, this is whether there is any key that would cause the given value (or another value for which `Equals()` from the given value returns `true`) to be generated immediately with the *current state* of the generator.

A return value of `true` means that there exists at least one key that could cause the value to be generated on the next call to `Generate()`, but does not necessarily guarantee that for *any* key. A return value of `false` means that there exists no key that could possibly cause the value to be generated. A return value of `null` means neither of the above promises can be made.

Any value returned by this method is invalidated if the internal state of this Generator changes after it is called.

When overriding this method, `null` is always a safe return value.

Parameters:
- `V` **`value`** - The value which should be checked.

Returns: See above.

## `CanGenerateFrom(K)`
`bool?` - Whether or not any value can be generated for a key without throwing an exception.

More specifically, this method checks whether the *current state* of the Generator can accept this key and return the value.

A return value of `true` means an immediate call to Generate with the given key will definitely succeed. A return value of `false` means an immediate call to Generate with the given key will definitely throw an exception. A return value of `null` means no such promises can be made either way.

Any value returned by this method is invalidated if the internal state of this Generator changes after it is called.

When overriding this method, `null` is always a safe return value.

Parameters:
- `K` **`key`** - The key which should be checked.

Returns: See above.

## `Generate(K)`
`V` - Generate a value for the specified key.

Parameters:
- `K` **`key`** - The key for which a value should be generated.

Returns: The generated value.

## `Wrap()`
`DictionaryGenerator<K, V>` - Creates an empty `DictionaryGenerator<K, V>` with this `Generator`.

Returns: The created `DictionaryGenerator<K, V>`.

## `Wrap(IDictionary<K, V>)`
`DictionaryGenerator<K, V>` - Creates a `DictionaryGenerator<K, V>` wrapping `dict` with this `Generator`.

Parameters:
- `IDictionary<K, V>` **`dict`** - The dictionary to be wrapped.

Returns: The created `DictionaryGenerator<K, V>`.