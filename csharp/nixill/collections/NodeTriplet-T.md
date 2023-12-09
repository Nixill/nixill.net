---
layout: page
title: NodeTriplet\<T\> class (Nixill.Collections)
permalink: /csharp/nixill/collections/NodeTriplet-T
---

The `NodeTriplet<T>` class is a class instantiated by the following methods:

- `AVLTreeDictionary<K, V>.EntriesAround(K key)` creates a `NodeTriplet<KeyValuePair<K, V>>`.
- `AVLTreeDictionary<K, V>.KeysAround(K key)` creates a `NodeTriplet<K>`.
- `AVLTreeSet<T>.SearchAround(T value)` creates a `NodeTriplet<T>`.

When created, it will contain:
- A lesser value, if the set/dictionary has a value/key lower than the one provided.
- An equal value, if the set/dictionary has a value/key equal to the one provided.
- A higher value, if the set/dictionary has a value/key higher than the one provided.

If the set/dictionary has no entries, then this will contain no values.

# Type Parameters
- `T`: The type of values contained in this `NodeTriplet<T>`.

# Properties
- `bool HasLesserValue` - `true` iff the `NodeTriplet<T>` contains a lesser value.
- `bool HasEqualValue` - `true` iff the `NodeTriplet<T>` contains an equal value.
- `bool HasHigherValue` - `true` iff the `NodeTriplet<T>` contains a higher value.
- `T LesserValue` - If the `NodeTriplet<T>` contains a lesser value, this retrieves that value. Otherwise, it throws an `InvalidOperationException`.
- `T EqualValue` - If the `NodeTriplet<T>` contains an equal value, this retrieves that value. Otherwise, it throws an `InvalidOperationException`.
- `T HigherValue` - If the `NodeTriplet<T>` contains a higher value, this retrieves that value. Otherwise, it throws an `InvalidOperationException`.