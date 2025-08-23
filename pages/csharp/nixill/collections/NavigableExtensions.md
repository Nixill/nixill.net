---
layout: page
title: NavigableExtensions class (Nixill.Collections)
permalink: /csharp/nixill/collections/NavigableExtensions
---

This class contains extension methods related to read-only navigable collections.

# Extension methods
## `INavigableDictionary<K, V>.AsReadOnly<K, V>`
`IReadOnlyNavigableDictionary<K, V>` - Wraps the INavigableDictionary in a read-only wrapper.

The wrapper is only a wrapper around the same dictionary, so code that retains a reference to the original may modify it and the changes will be reflected under the wrapper.

Type parameters:
- `K` - The type of keys in the dictionary
- `V` - The type of values in the dictionary

Parameters:
- `this INavigableDictionary<K, V>` **`dict`** - The dictionary to be wrapped.

Returns: The aforementioned wrapper.

## `INavigableSet<T>.AsReadOnly<T>`
`IReadOnlyNavigableSet<T>` - Wraps the INavigableSet in a read-only wrapper.

The wrapper is only a wrapper around the same set, so code that retains a reference to the original may modify it and the changes will be reflected under the wrapper.

Type parameters:
- `K` - The type of keys in the dictionary
- `V` - The type of values in the dictionary

Parameters:
- `this INavigableSet<T>` **`set`** - The set to be wrapped.

Returns: The aforementioned wrapper.