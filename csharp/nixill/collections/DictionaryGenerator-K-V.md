---
layout: page
title: DictionaryGenerator\<K, V\> class (Nixill.Collections)
permalink: /csharp/nixill/collections/DictionaryGenerator-K-V
---

A `DictionaryGenerator<K, V>` wraps around an `IDictionary<K, V>` to add automatic generation of values from keys when a key not in the dictionary is retrieved.

# Type parameters
- `K`: The type of keys contained within the dictionary.
- `V`: The type of values contained within the dictionary.

# Constructors
This class contains three constructor overloads:

- `()` - Creates a new `Dictionary<K, V>` and uses a new `DefaultGenerator<K, V>` on it.
- `(Generator<K, V>)` - Creates a new `Dictionary<K, V>` and uses the specified `Generator<K, V>` on it.
- `(IDictionary<K, V>, Generator<K, V>)` - Wraps an existing `IDictionary<K, V>` and uses the specified `Generator<K, V>` on it.

# Properties
## `this[K]`
`V` - Gets or sets the value associated with the specified key.

If the specified key is not found, a get operation will automatically generate a value, store it to that key in the dictionary, and return it.

## `Count`
`int` - Gets the number of elements in the underlying `IDictionary<K, V>`.

## `Dict`
`IDictionary<K, V>` - Gets the `IDictionary<K, V>` wrapped by this generator.

## `Generator`
`Generator<K, V>` - Gets the generator used by this `DictionaryGenerator<K, V>`.

## `IsReadOnly`
`bool` - Gets whether or not the underlying `IDictionary<K, V>` is read-only.

## `Keys`
`ICollection<K>` - Gets a collection of the keys contained in the underlying `IDictionary<K, V>`.

## `Values`
`ICollection<V>` - Gets a collection of the values contained in the underlying `IDictionary<K, V>`.

# Methods
## New to this type
### `Add(K)`
`V` - Adds an entry to the dictionary with the specified key, using an automatically-generated value.

Parameters:
- `K` **`key`** - The key for which to generate a value and add it to the dictionary.

Returns: The generated value.

Exceptions:
- `ArgumentNullException` - If `key` is `null`.
- `ArgumentException` - If `key` already exists within the dictionary.

### `CanGenerateForKey(K)`
`bool?` - Returns whether or not the attached `Generator<K, V>` can generate a value for the specified key without throwing an exception.

See `Generator<K, V>.CanGenerateFrom(K)` for return value details.

This method does not check current dictionary contents. In particular, it may return `true` for keys already contained within the dictionary.

Parameters:
- `K` **`key`** - The key to check for.

### `CanGenerateValue(V)`
`bool?` - Returns whether or not a specific value can be generated immediately.

See `Generator<K, V>.CanGenerate(V)` for return value details.

This method does not check current dictionary contents. In particular, it may return `true` for values already contained in the dictionary, and may also return `false` for values already contained in the dictionary (whether or not the generator generated them in the past).

Parameters:
- `V` **`value`** - The value to check for.

### `TryGetValue(K, out V)`
`bool` - Attempts to get *or generate* the value for the specified key.

This method will only return `false` when a value cannot be generated. If a key doesn't exist but a value can be generated for it, it will do so.

Parameters:
- `K` **`key`** - The key for which a value should be obtained.
- `out V` **`value`** - When the method returns `true`, this contains the value that the dictionary contains at the specified key (regardless of whether it existed before or was newly generated). When the methods returns `false`, this contains the default value for its type.

Returns: `true` iff the specified key was already contained in the dictionary *or* a value could be generated for it; `false` otherwise.

## Inherited from `IDictionary<K, V>`
- `void Add(K key, V value)` - Adds the specified key and value to the underlying dictionary.
- `void Add(KeyValuePair<K, V> entry)` - Adds the specified entry to the underlying dictionary.
- `void Clear()` - Clears the underlying dictionary.
- `bool ContainsKey(K key)` - Returns whether or not the underlying dictionary contains an entry with the given key.
- `bool Contains(KeyValuePair<K, V> entry)` - Returns whether or not the underlying dictionary contains an entry with the given key and value.
- `void CopyTo(KeyValuePair<K, V>[] array, int index)` - Copies entries of the underlying dictionary to a `KeyValuePair<K, V>` array.
- `IEnumerator<KeyValuePair<K, V>> GetEnumerator()` - Gets an enumerator over the entries of the underlying dictionary.
- `IEnumerator IEnumerable.GetEnumerator()` - Gets a non-generic enumerator over the entries of the underlying dictionary.
- `bool Remove(K key)` - If the underlying dictionary has an entry with the key `key`, removes it and returns `true`. Otherwise, returns `false`.
- `bool Remove(KeyValuePair<K, V> entry)` - If the underlying dictionary has an entry with the key and value of `entry`, removes it and returns `true`. Otherwise, returns `false`.
- `bool TryGetValue(K key, out V value)` - 