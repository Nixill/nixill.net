---
layout: page
title: INavigableSet\<T\> interface (Nixill.Collections)
permalink: /csharp/nixill/collections/INavigableSet-T
---

A sorted set that can be navigated using methods such as `Lower`, `Floor`, `Ceiling`, and `Higher`.

Extends `ISet<T>`.

# Methods
For all of these methods:
- "lowest" refers to the lowest value in the set.
- "lower" refers to the highest value *less than* the given value.
- "floor" refers to the highest value *less than or equal to* the given value.
- "ceiling" refers to the lowest value *greater than or equal to* the given value.
- "higher" refers to the lowest value *greater than* the given value.
- "highest" refers to the highest value in the set.
- "a relative value" just refers to whichever of those is applicable to the particular methods in question.

# `Lower`, `Floor`, `Ceiling`, `Higher`
`T` - Returns a value relative to the specified value.

Parameters:
- `T` **`from`** - The value relative to which another should be found.

Returns: The relative value.

Exceptions:
- `ArgumentOutOfRangeException` - No such relative value exists.
- `ArgumentNullException` - `from` is null.
- `InvalidOperationException` - No values exist in the set.

# `ContainsLower`, `ContainsFloor`, `ContainsCeiling`, `ContainsHigher`
`bool` - Returns whether or not the set contains a value relative to the specified value.

Parameters:
- `T` **`from`** - The value relative to which another should be checked for existence.

Returns: `true` iff the relative value exists, `false` otherwise.

# `TryGetLower`, `TryGetFloor`, `TryGetCeiling`, `TryGetHigher`
`bool` - Returns whether or not the set contains a value relative to the specified value, and sets a parameter if so.

Parameters:
- `T` **`from`** - The value relative to which another should be checked for existence.
- `out T` **`value`** - When this method returns `true`, this contains the relative value. Otherwise, this contains the default value for the type.

# `LowestValue`, `HighestValue`
`T` - Returns the lowest or highest value in the set.

Parameters: None

Returns: The lowest or highest value in the set.

Exceptions:
- `InvalidOperationException` - No values exist in the set.