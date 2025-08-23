---
layout: page
title: INavigableDictionary\<K, V\> interface (Nixill.Collections)
permalink: /csharp/nixill/collections/INavigableDictionary-K-V
---

A sorted dictionary that can be navigated using methods such as `Lower`, `Floor`, `Ceiling`, and `Higher`.

Extends `IDictionary<T>`.

# Methods
For all of these methods:
- "lowest" refers to the lowest key in the set.
- "lower" refers to the highest key *less than* the given key.
- "floor" refers to the highest key *less than or equal to* the given key.
- "ceiling" refers to the lowest key *greater than or equal to* the given key.
- "higher" refers to the lowest key *greater than* the given key.
- "highest" refers to the highest key in the set.
- "a relative key" just refers to whichever of those is applicable to the particular methods in question.

# `LowerKey`, `FloorKey`, `CeilingKey`, `HigherKey`
`K` - Returns a key relative to the specified key.

Parameters:
- `K` **`from`** - The key relative to which another should be found.

Returns: The relative key.

Exceptions:
- `ArgumentOutOfRangeException` - No such relative key exists.
- `ArgumentNullException` - `from` is null.
- `InvalidOperationException` - No entries exist in the set.

# `LowerEntry`, `FloorEntry`, `CeilingEntry`, `HigherEntry`
`KeyValuePair<K, V>` - Returns an entry with a key relative to the specified key.

Parameters:
- `K` **`from`** - The key relative to which another should be found.

Returns: The relative entry.

Exceptions:
- `ArgumentOutOfRangeException` - No such relative key exists.
- `ArgumentNullException` - `from` is null.
- `InvalidOperationException` - No entries exist in the set.

# `ContainsLower`, `ContainsFloor`, `ContainsCeiling`, `ContainsHigher`
`bool` - Returns whether or not the set contains a key relative to the specified key.

Parameters:
- `T` **`from`** - The key relative to which another should be checked for existence.

Returns: `true` iff the relative entry exists, `false` otherwise.

# `TryGetLowerKey`, `TryGetFloorKey`, `TryGetCeilingKey`, `TryGetHigherKey`
`bool` - Returns whether or not the set contains a key relative to the specified key, and sets a parameter to it if so.

Parameters:
- `T` **`from`** - The key relative to which another should be checked for existence.
- `out T` **`value`** - When this method returns `true`, this contains the relative key. Otherwise, this contains the default value for the type.

# `TryGetLowerEntry`, `TryGetFloorEntry`, `TryGetCeilingEntry`, `TryGetHigherEntry`
`bool` - Returns whether or not the set contains an entry with a key relative to the specified key, and sets a parameter to it if so.

Parameters:
- `T` **`from`** - The key relative to which another should be checked for existence.
- `out KeyValuePair<K, V>` **`value`** - When this method returns `true`, this contains the entry of the relative key. Otherwise, this contains the default value for the type.

# `LowestValue`, `HighestValue`
`T` - Returns the lowest or highest value in the set.

Parameters: None

Returns: The lowest or highest value in the set.

Exceptions:
- `InvalidOperationException` - No values exist in the set.

# `LowestValue`, `HighestValue`
`T` - Returns the lowest or highest value in the set.

Parameters: None

Returns: The lowest or highest value in the set.

Exceptions:
- `InvalidOperationException` - No values exist in the set.