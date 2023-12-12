---
layout: page
title: EnumerableUtils class (Nixill.Utils)
permalink: /csharp/nixill/utils/EnumerableUtils
---

Utilities and extension methods for working with IEnumerables.

`public static class EnumerableUtils`

# Static methods
## `Of<T>(T)`
`IEnumerable<T>` - Enumerates over a single item.

Type parameters:
- `T` - The type of the object.

Parameters:
- `T` **`item`** - The item to enumerate once.

Returns: An enumerable containing the specified item exactly once.

## `Of<T>(T...)`
`IEnumerable<T>` - Enumerates over multiple items.

For security, this method does not simply return its original parameter (which would satisfy the return type), but copies it through a `yield return` function.

Type parameters:
- `T` - The type of the object.

Parameters:
- `params T` **`items`** - The items to enumerate.

## `Repeat<T>(Func<T>, int)`
`IEnumerable<T>` - Runs a function multiple times, enumerating over its outputs.

Type parameters:
- `T` - The type of generated objects.

Parameters:
- `Func<T>` **`func`** - The function to run.
  - Returns: Anything.
- `int` **`count`** - The number of times to run the function.

Returns: An enumerable containing the output of running `func` `count` times.

## `RepeatInfinite<T>(Func<T>)`
`IEnumerable<T>` - Runs a function infinitely, enumerating over its outputs.

**Produces infinite output. Do not use with methods that instantly enumerate a whole enumerable.**

Type parameters:
- `T` - The type of generated objects.

Parameters:
- `Func<T>` **`func`** - The function to run.
  - Returns: Anything.

Returns: An enumerable containing **infinite output**, the result of running `func` indefinitely.

## `RepeatInfinite<T>(T)`
`IEnumerable<T>` - Copies an object infinitely, enumerating over it repeatedly.

**Produces infinite output. Do not use with methods that instantly enumerate a whole enumerable.**

Type parameters:
- `T` - The type of copied objects.

Parameters:
- `T` **`item`** - The item to copy.

Returns: An enumerable containing **infinite output**, the result of copying `item` indefinitely.

# Extension methods
## `IEnumerable<T>.AggregateFromFirst<T>(Func<T, T, T>)`
`T` - Aggregates together a series of elements, skipping the first element and instead using it directly as the seed.

Type parameters:
- `T` - The type of elements in the series.

Parameters:
- `this IEnumerable<T>` **`elems`** - The sequence to aggregate.
- `Func<T, T, T>` **`aggregation`** - The aggregation function.
  - `T` - The existing aggregate up to this point in the sequence.
  - `T` - The next item in sequence.
  - Returns: `T` - The aggregate of all those items plus the next.

Returns: The aggregate of all the items.

Exceptions:
- `InvalidOperationException` - If the sequence contains no elements.

## `IEnumerable<TSource>.ChunkWhile<TSource>(Func<TSource, bool>, bool, bool, bool)`
`IEnumerable<IEnumerable<TSource>>` - Splits the original enumerable up into chunks of consecutive objects that satisfy a condition.

Remarks: Each single chunk is enumerated all at once and stored into a list; those lists are `yield return`ed by this function. When there's a large chunk of values that satisfy the condition, this method will not yield until one that doesn't is found. Use caution when using infinite enumerables with this method.

Type parameters:
- `TSource` - The type of objects in the enumerable.

Parameters:
- `this IEnumerable<T>` **`items`**: The original enumerable.
- `Func<TSource, bool>` **`predicate`**: The condition that must be satisfied by consecutive items to form one chunk.
  - `TSource` - The item being checked for the condition.
  - Returns `bool` - Whether or not that item passes the condition.
- `bool` **`appendFails`** = false: Whether or not an item that fails the predicate should be appended to the chunk it ends.
- `bool` **`prependFails`** = false: Whether or not an item that fails the predicate should be prepended to the chunk it starts.
- `bool` **`skipEmpty`** = false: Whether or not empty chunks should be skipped.

Returns: An enumerable containing chunks as described above.

## `IEnumerable<TSource>.ChunkWhile<TSource>(Func<TSource, TSource, bool>, TSource, bool, bool, bool)`
`IEnumerable<IEnumerable<TSource>>` - Splits the original enumerable up into chunks of consecutive objects that satisfy a condition.

Remarks: Each single chunk is enumerated all at once and stored into a list; those lists are `yield return`ed by this function. When there's a large chunk of values that satisfy the condition, this method will not yield until one that doesn't is found. Use caution when using infinite enumerables with this method.

Type parameters:
- `TSource` - The type of objects in the enumerable.

Parameters:
- `this IEnumerable<T>` **`items`**: The original enumerable.
- `Func<TSource, TSource, bool>` **`predicate`**: The condition that must be satisfied by consecutive items.
  - `TSource` - The *previous* item in the list. Defaults to `firstComparison`.
  - `TSource` - The item being checked for the condition.
  - Returns `bool` - Whether or not that item passes the condition.
- `TSource` **`firstComparison`** = default(TSource) - The value that should be "previous" to the first item in the list.
- `bool` **`appendFails`** = false - Whether or not an item that fails the predicate should be appended to the chunk it ends.
- `bool` **`prependFails`** = false - Whether or not an item that fails the predicate should be prepended to the chunk it starts.
- `bool` **`skipEmpty`** = false - Whether or not empty chunks should be skipped.

Returns: An enumerable containing chunks as described above.

## `IEnumerable<T>.Do<T>(Action<T>)`
`void` - Performs an action for every item in the list.

Type parameters:
- `T` - The type of objects in the enumerable.

Parameters:
- `this IEnumerable<T>` **`list`**: The original enumerable.
- `Action<T>` **`act`**: The action to perform.
  - `T`: The item from `list`.

## `IEnumerable<T>.Do<T>(Action<T, int>)`
`void` - Performs an action for every item in the list.

Type parameters:
- `T` - The type of objects in the enumerable.

Parameters:
- `this IEnumerable<T>` **`list`**: The original enumerable.
- `Action<T, int>` **`act`**: The action to perform.
  - `T`: The item from `list`.
  - `int`: The index of the item within the enumerable.

## `IEnumerable<char>.FormString()`
`string` - Creates a string out of a char enumerable.

Parameters:
- `this IEnumerable<char>` **`chars`**: The original char enumerable.

Returns: The string formed by the enumerated chars.

## `IEnumerable<T>.MinMany<T>()`
`IEnumerable<T>` - Enumerates over all items in `list` that have the minimum value.

Type parameters:
- `T` - The type of objects in the enumerable. Implements `IComparable<T>`.

Parameters:
- `this IEnumerable<T>` **`list`**: The original enumerable.

Returns: An enumerable over all objects from `list` that have the minimum value.

## `IEnumerable<T>.MinMany<T>(IComparer<T>)`
`IEnumerable<T>` - Enumerates over all items in `list` that have the minimum value.

Type parameters:
- `T` - The type of objects in the enumerable.

Parameters:
- `this IEnumerable<T>` **`list`**: The original enumerable.
- `IComparer<T>` **`cmp`**: A comparer for the objects.

Returns: An enumerable over all objects from `list` that have the minimum value.

## `IEnumerable<TSource>.MinManyBy<TSource, TResult>(Func<TSource, TResult>)`
`IEnumerable<TSource>` - Enumerates over all items in `list` that map to the minimum value.

Type parameters:
- `TSource` - The type of objects in the enumerable.
- `TResult` - The type of objects they become. Implements `IComparable<T>`.

Parameters:
- `this IEnumerable<TSource>` **`list`**: The original enumerable.
- `Func<TSource, TResult>` **`mutator`**: A function that turns the objects into the value actually compared.
  - `TSource`: The original input object from `list`.
  - Returns `TResult`: The value to compare.

Returns: An enumerable over all objects from `list` that map to the minimum value.

## `IEnumerable<TSource>.MinManyBy<TSource, TResult>(Func<TSource, TResult>, IComparer<TResult>)`
`IEnumerable<TSource>` - Enumerates over all items in `list` that map to the minimum value.

Type parameters:
- `TSource` - The type of objects in the enumerable.
- `TResult` - The type of objects they become.

Parameters:
- `this IEnumerable<TSource>` **`list`**: The original enumerable.
- `Func<TSource, TResult>` **`mutator`**: A function that turns the objects into the value actually compared.
  - `TSource`: The original input object from `list`.
  - Returns `TResult`: The value to compare.
- `IComparer<TResult>` **`cmp`**: A comparer for the values.

Returns: An enumerable over all objects from `list` that map to the minimum value.

## `IEnumerable<T>.MaxMany<T>()`
`IEnumerable<T>` - Enumerates over all items in `list` that have the maximum value.

Type parameters:
- `T` - The type of objects in the enumerable. Implements `IComparable<T>`.

Parameters:
- `this IEnumerable<T>` **`list`**: The original enumerable.

Returns: An enumerable over all objects from `list` that have the maximum value.

## `IEnumerable<T>.MaxMany<T>(IComparer<T>)`
`IEnumerable<T>` - Enumerates over all items in `list` that have the maximum value.

Type parameters:
- `T` - The type of objects in the enumerable.

Parameters:
- `this IEnumerable<T>` **`list`**: The original enumerable.
- `IComparer<T>` **`cmp`**: A comparer for the objects.

Returns: An enumerable over all objects from `list` that have the maximum value.

## `IEnumerable<TSource>.MaxManyBy<TSource, TResult>(Func<TSource, TResult>)`
`IEnumerable<TSource>` - Enumerates over all items in `list` that map to the maximum value.

Type parameters:
- `TSource` - The type of objects in the enumerable.
- `TResult` - The type of objects they become. Implements `IComparable<T>`.

Parameters:
- `this IEnumerable<TSource>` **`list`**: The original enumerable.
- `Func<TSource, TResult>` **`mutator`**: A function that turns the objects into the value actually compared.
  - `TSource`: The original input object from `list`.
  - Returns `TResult`: The value to compare.

Returns: An enumerable over all objects from `list` that map to the maximum value.

## `IEnumerable<TSource>.MaxManyBy<TSource, TResult>(Func<TSource, TResult>, IComparer<TResult>)`
`IEnumerable<TSource>` - Enumerates over all items in `list` that map to the maximum value.

Type parameters:
- `TSource` - The type of objects in the enumerable.
- `TResult` - The type of objects they become.

Parameters:
- `this IEnumerable<TSource>` **`list`**: The original enumerable.
- `Func<TSource, TResult>` **`mutator`**: A function that turns the objects into the value actually compared.
  - `TSource`: The original input object from `list`.
  - Returns `TResult`: The value to compare.
- `IComparer<TResult>` **`cmp`**: A comparer for the values.

Returns: An enumerable over all objects from `list` that map to the maximum value.

## `IEnumerable<T>.Permutations<T>(int)`
`IEnumerable<IEnumerable<T>>` - Exhaustively returns an enumeration over all possible orderings of the original enumeration.

Note that this method doesn't check equality of elements, and will return duplicate orders for sequences with duplicate elements. For example, `"121".Permutations()` returns the orderings `121`, `112`, `211`, `211`, `112`, `121`, in that order. To exclude duplicates, use `PermutationsDistinct()` instead.

Type parameters:
- `T` - The type of objects in the list.

Parameters:
- `this IEnumerable<TSource>` **`elems`** - The original enumerable.
- `int` **`limit`** = 0 - The maximum number of elements to select in each permutation. For `limit <= 0`, all but -limit items will be taken instead (this also means that limit=0 will select the whole list).

Returns: An enumerable that contains the original enumerable with its elements arranged in every possible order.

## `IEnumerable<T>.PermutationsDistinct<T>(int)`
`IEnumerable<IEnumerable<T>>` - Returns an enumeration over all possible distinct orderings of the original enumeration.

This method checks equality of elements, and will not return duplicate orders for sequences with duplicate elements. For example, `"121".PermutationsDistinct()` returns the orderings `121`, `112`, `211`, in that order. To include duplicates, use `Permutations()` instead.

Type parameters:
- `T` - The type of objects in the list.

Parameters:
- `this IEnumerable<TSource>` **`elems`** - The original enumerable.
- `int` **`limit`** = 0 - The maximum number of elements to select in each permutation. For `limit <= 0`, all but -limit items will be taken instead (this also means that limit=0 will select the whole list).

Returns: An enumerable that contains the original enumerable with its elements arranged in every possible distinct order.

## `IList<T>.Pop()`
`T` - Removes the first item from a list and returns it.

Parameters:
- `this IList<T>` **`list`** - The listt from which to remove an item.

Returns: The removed item from the list.

## `IEnumerable<TLeft>.Product<TLeft, TRight>(IEnumerable<TRight>)`
`IEnumerable<(TLeft, TRight)>` - Enumerates over every combination of an item from `left` and an item from `right`, returning the pairs directly.

Type parameters:
- `TLeft` - The type of the left enumerable.
- `TRight` - The type of the right enumerable.

Parameters:
- `this IEnumerable<TLeft>` **`left`**: The original enumerable.
- `IEnumerable<TRight>` **`right`**: The enumerable to combine it with.

Returns: An enumerable over all the combined objects.

## `IEnumerable<TLeft>.Product<TLeft, TRight, TResult>(IEnumerable<TRight>, Func<TLeft, TRight, TResult>)`
`IEnumerable<TResult>` - Enumerates over every combination of an item from `left` and an item from `right`.

Type parameters:
- `TLeft` - The type of the left enumerable.
- `TRight` - The type of the right enumerable.
- `TResult` - The output type.

Parameters:
- `this IEnumerable<TLeft>` **`left`**: The original enumerable.
- `IEnumerable<TRight>` **`right`**: The enumerable to combine it with.
- `Func<TLeft, TRight, TResult>` **`func`**: Converts each pair of objects into a magical third object.
  - `TLeft`: The item from `left` that is being combined.
  - `TRight`: The item from `right` that is being combined.
  - Returns: An object representing the combination of the two.

Returns: An enumerable over all the combined objects.

## `IEnumerable<T>.Repeat(int)`
`IEnumerable<T>` - Enumerates over a sequence, concatenated to itself for a total of `count` loops.

For example, `new char[] {'a', 'b'}.Repeat(5)` will output an enumerable over `{'a', 'b', 'a', 'b', 'a', 'b', 'a', 'b', 'a', 'b'}`.

Type parameters:
- `T` - The type of objects in the enumerable.

Parameters:
- `this IEnumerable<T>` **`seq`** - The sequence to repeat.
- `int` **`count`** - The number of times to repeat the sequence.

Returns: An enumerable over the repeating sequence.

## `IEnumerable<T>.RepeatInfinite()`
`IEnumerable<T>` - Enumerates over a sequence, concatenated to itself infinitely.

For example, `new char[] {'a', 'b'}.RepeatInfinite()` will output an enumerable over `{'a', 'b', 'a', 'b', 'a', 'b', …`.

**Produces infinite output. Do not use with methods that instantly enumerate a whole enumerable.**

Type parameters:
- `T` - The type of objects in the enumerable.

Parameters:
- `this IEnumerable<T>` **`seq`** - The sequence to repeat.

Returns: An enumerable over **infinite output**, repeating the original sequence indefinitely.

## `IEnumerable<TSource>.WhereOrdered<T>(bool, bool)`
`IEnumerable<T>` - Enumerates over objects in `sequence` that are larger than the previously yielded objects.

Type parameters:
- `T` - The type of objects in the enumerable. Should implement `IComparable<T>`, but this is not compiler-enforced.

Parameters:
- `this IEnumerable<T>` **`sequence`**: The sequence to enumerate.
- `bool` **`desc`** = false - If `true`, only objects *smaller* than previously yielded objects should be yielded.
- `bool` **`distinctly`** = false - If `false`, also yield objects *equal to* the last yielded object.

Returns: An enumerable that limits the original's objects as described above.

## `IEnumerable<T>.WhereOrderedBy<T>(IComparer<T>, bool, bool)`
`IEnumerable<T>` - Enumerates over objects in `sequence` that are larger than the previously yielded objects.

Type parameters:
- `T` - The type of objects in the enumerable.

Parameters:
- `this IEnumerable<T>` **`sequence`**: The sequence to enumerate.
- `IComparer<T>` **`comparer`** - The comparer to compare items in the sequence.
- `bool` **`desc`** = false - If `true`, only objects *smaller* than previously yielded objects should be yielded.
- `bool` **`distinctly`** = false - If `false`, also yield objects *equal to* the last yielded object.

Returns: An enumerable that limits the original's objects as described above.

## `IEnumerable<TSource>.WhereOrderedBy<TSource, TKey>(Func<TSource, TKey>, bool, bool)`
`IEnumerable<TSource>` - Enumerates over objects in `sequence` that are larger than the previously yielded objects.

Type parameters:
- `TSource` - The type of objects in the enumerable.
- `TKey` - The type of values being compared. Should implement `IComparable<TKey>`, but this is not compiler-enforced.

Parameters:
- `this IEnumerable<TSource>` **`sequence`**: The sequence to enumerate.
- `Func<TSource, TKey>` **`mutator`**: The function that generates values to compare.
  - `TSource`: The original item from `sequence`.
  - Returns `TKey`: The value that's actually compared.
- `bool` **`desc`** = false - If `true`, only objects *smaller* than previously yielded objects should be yielded.
- `bool` **`distinctly`** = false - If `false`, also yield objects *equal to* the last yielded object.

Returns: An enumerable that limits the original's objects as described above.

## `IEnumerable<TSource>.WhereOrderedBy<TSource, TKey>(Func<TSource, TKey>, IComparer<TKey>, bool, bool)`
`IEnumerable<TSource>` - Enumerates over objects in `sequence` that are larger than the previously yielded objects.

Type parameters:
- `TSource` - The type of objects in the enumerable.
- `TKey` - The type of values being compared.

Parameters:
- `this IEnumerable<TSource>` **`sequence`**: The sequence to enumerate.
- `Func<TSource, TKey>` **`mutator`**: The function that generates values to compare.
  - `TSource`: The original item from `sequence`.
  - Returns `TKey`: The value that's actually compared.
- `IComparer<TKey>` **`comparer`** - The comparer to compare items in the sequence.
- `bool` **`desc`** = false - If `true`, only objects *smaller* than previously yielded objects should be yielded.
- `bool` **`distinctly`** = false - If `false`, also yield objects *equal to* the last yielded object.

Returns: An enumerable that limits the original's objects as described above.

## `IEnumerable<T>.WithIndex()`
`IEnumerable<(T Item, int Index)>` - Adds the index to each element in a sequence. `x.WithIndex()` is a shortcut for `x.Select((x, i) => (x, i))`.

Type parameters:
- `T` - The type of elements in the original sequence.

Parameters:
- `this IEnumerable<T>` **`original`** - The original sequence.

Returns: Tuples of:
- `T` - An original item from the sequence.
- `int` - That item's index within the sequence.