---
layout: page
title: AVLTreeDictionary\<K, V\> class (Nixill.Collections)
permalink: /csharp/nixill/collections/AVLTreeDictionary-K-V
---

The `AVLTreeDictionary<K, V>` class is a navigable key-value dictionary backed by an AVL binary tree. It is an automatically sorted dictionary inspired by Java's [`TreeMap<K, V>`](https://docs.oracle.com/javase/8/docs/api/java/util/TreeMap.html) class, created because C#'s native [`SortedDictionary<TKey, TValue>`](https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic.sorteddictionary-2) lacks key trawling and searching methods.

This particular implementation is backed by an `AVLTreeSet<KeyValuePair<K, V>>`, with a comparer that runs the given comparison function only on the elements' keys, ignoring values entirely.

# Type parameters
- `K`: The type of the keys stored in the dictionary.
- `V`: The type of the values stored in the dictionary.

# Constructors
This class contains six constructor overloads:

- `()`
- `(IComparer<K>)`
- `(Comparison<K>)`
- `(IEnumerable<KeyValuePair<K, V>>)`
- `(IEnumerable<KeyValuePair<K, V>>, IComparer<K>)`
- `(IEnumerable<KeyValuePair<K, V>>, Comparison<K>)`

The parameters of these constructors are as follows:

- `IEnumerable<KeyValuePair<K, V>>` **`elems`**: The elements with which to pre-populate the dictionary. Overloads that don't have this parameter create an empty `AVLTreeDictionary`.
- `IComparer<K>` **`comparer`** *or* `Comparison<K>` **`comparer`**: The comparer or function that compares the keys of this dictionary. Overloads that don't have either of these parameters use `K`'s natural comparer, and throw an `InvalidOperationException` if `K` isn't naturally comparable.

# Properties
This class contains the following properties:

## `this[K]`
`V` - Get or set the element with the specified key.

### Parameters
- `K` **`key`**: The key of the element to get or set.

### Exceptions
- `ArgumentNullException`: `key` is null.
- `KeyNotFoundException`: The property is being read, but `key` is not in the dictionary.

## `Count`
`int` - Gets the number of items contained in the `AVLTreeDictionary<K, V>`.

## `IsReadOnly`
`bool` - Gets whether or not this `AVLTreeDictionary<K, V>` is read-only (which is always `false`).

## `Keys`
`ICollection<K>` - Gets an `ICollection<T>` containing the keys of the `AVLTreeDictionary<K, V>`.

The order of the keys in this collection is smallest to largest.

## `Values`
`ICollection<V>` - Gets an `ICollection<T>` containing the values of the `AVLTreeDictionary<K, V>`.

The order of the values in this collection is the values of the smallest to largest keys.

# Methods
This class contains the following methods:

## Empty check
The `IsEmpty()` method simply returns `true` iff the `AVLTreeDictionary<K, V>` contains no elements, and `false` otherwise.

## Nearby keys/entries
The `EntriesAround(K)` and `KeysAround(K)` methods take a `K` for the parameter **`from`**, and return a `NodeTriplet<KeyValuePair<K, V>>` or `NodeTriplet<K>` respectively, with the triplet's lower, equal, and higher values equal to the entries of the lower, equal, or higher keys respectively.

⚠ Due to a bug, `KeysAround` will return the lower key or lack thereof for all three parts of the triplet up to version 0.9.4.

## Navigation
Through the `INavigableDictionary<K, V>` interface, `AVLTreeDictionary<K, V>` implements several methods for getting keys and entries higher or lower than a given key.

For all of these methods:
- "lowest" refers to the lowest key in the dictionary.
- "lower" refers to the highest key *less than* the given value.
- "floor" refers to the highest key *less than or equal to* the given value.
- "ceiling" refers to the lowest key *greater than or equal to* the given value.
- "higher" refers to the lowest key *greater than* the given value.
- "highest" refers to the highest key in the dictionary.
- "a relative key" just refers to whichever of those is applicable to the particular method in question.

### Contains relative key
The methods `ContainsLower(K)`, `ContainsFloor(K)`, `ContainsCeiling(K)`, and `ContainsHigher(K)` are all `bool`s.

These methods have one parameter, `K` **`from`**, which is the key relative to which another should be found.

They return `true` iff such a relative key exists, and `false` otherwise.

### Try get relative key/entry
The methods `TryGetLowerEntry`, `TryGetLowerKey`, `TryGetFloorEntry`, `TryGetFloorKey`, `TryGetCeilingEntry`, `TryGetCeilingKey`, `TryGetHigherEntry`, and `TryGetHigherKey` are all `bool`s.

These methods have two parameters:
- `K` **`from`** - The key relative to which another should be found.
- For the `Entry` methods: `out KeyValuePair<K, V>` **`entry`** - When the method returns `true`, this contains the found entry. When the method returns `false`, this contains an entry with the default values for the types.
- For the `Key` methods: `out K` **`key`** - When the method returns `true`, this contains the found key. When the method returns `false`, this contains the default value for the key's type.

They return `true` iff such a relative key exists, as well as setting `entry` or `key` to that entry or key, and `false` otherwise.

### Get relative entry/key
The methods `LowerEntry`, `LowerKey`, `FloorEntry`, `FloorKey`, `CeilingEntry`, `CeilingKey`, `HigherEntry`, or `HigherKey` all directly get a relative key or its entry.

All of these methods have one parameter, `K` **`from`**, which is the key relative to which another should be found.

The `Key` variants return a `K`, which is the relative key. The `Entry` variants return a `KeyValuePair<K, V>`, which is that key's entry.

If the relative key doesn't exist, these methods throw an exception:
- `InvalidOperationException`: If the `AVLTreeDictionary<K, V>` is empty.
- `ArgumentOutOfRangeException`: If there is no such relative key.

### Get bounding key/entry
The methods `LowestEntry`, `LowestKey`, `HighestEntry`, and `HighestKey` return the bounding keys or their entries.

All of these methods are parameterless.

The `Key` variants return a `K`, which is the bounding key. The `Entry` variants return a `KeyValuePair<K, V>`, which is that key's entry.

If the `AVLTreeDictionary<K, V>` is empty, an `InvalidOperationException` is thrown.

## Regular Dictionary methods
These methods function the same as a regular `Dictionary<K, V>`, so I'll just summarize them here:

- `Add(K key, V value)`: If the dictionary doesn't already contain `key`, adds `key`/`value` to the dictionary. Otherwise, throws an `ArgumentException`.
- `ContainsKey(K key)`: Returns true iff the dictionary contains `key`, and false otherwise.
- `Remove(K key)`: If the dictionary contains `key`, removes that entry and returns `true`. Otherwise, returns `false`.
- `TryGetValue(K key, out V value)`: If the dictionary contains `key`, sets `value` to that value and returns `true`. Otherwise, returns `false`.
- `Add(KeyValuePair<K, V> entry)`: Adds the `entry` to the dictionary, replacing another with the same `entry.Key` if necessary.
- `Clear()`: Clears the dictionary entirely.
- `Contains(KeyValuePair<K, V> entry)`: Returns true iff the dictionary contains exactly the given entry (key and value must both match).
- `CopyTo(KeyValuePair<K, V>[] array, int index)`: Copies the dictionary's entries into an array.
- `Remove(KeyValuePair<K, V> entry)`: If the dictionary contains `entry` (both key and value must match), removes that entry and returns `true`. Otherwise, returns `false`.
- `GetEnumerator()`: Returns an `IEnumerator<KeyValuePair<K, V>>` over the dictionary's entries.
- `IEnumerable.GetEnumerator()`: Returns a non-generic `IEnumerator` over the dictionary's entries.
