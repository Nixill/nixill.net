---
layout: page
title: DictionaryGeneratorExtensions class (Nixill.Collections)
permalink: /csharp/nixill/collections/DictionaryGeneratorExtensions
---

This class contains extension methods relating to `DictionaryGenerator<K, V>`s.

# Extension methods
## `IDictionary<K, V>.CopyWithGenerator<K, V>(Generator<K, V>)`
`DictionaryGenerator<K, V>` - Creates a `DictionaryGenerator<K, V>` that wraps a copy of the existing dictionary with a specified generator.

Type parameters:
- `K` - The type of keys in the dictionary
- `V` - The type of values in the dictionary

Parameters:
- `this IDictionary<K, V>` **`dict`** - The dictionary to be copied and wrapped
- `Generator<K, V>` **`gen`** - The generator to use

Returns: The wrapping `DictionaryGenerator<K, V>`, which will not modify `dict`.

## `IDictionary<K, V>.WithGenerator<K, V>(Generator<K, V>)`
`DictionaryGenerator<K, V>` - Creates a `DictionaryGenerator<K, V>` that wraps the existing dictionary with a specified generator.

Type parameters:
- `K` - The type of keys in the dictionary
- `V` - The type of values in the dictionary

Parameters:
- `this IDictionary<K, V>` **`dict`** - The dictionary to be wrapped
- `Generator<K, V>` **`gen`** - The generator to use

Returns: The wrapping `DictionaryGenerator<K, V>`, which will modify `dict`.