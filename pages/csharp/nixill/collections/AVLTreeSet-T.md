---
layout: page
title: AVLTreeSet\<T\> class (Nixill.Collections)
permalink: /csharp/nixill/collections/AVLTreeSet-T
---

The `AVLTreeSet<T>` class is a navigable key set backed by an AVL binary tree. It is an automatically sorted set inspired by Java's [`TreeSet<E>`](https://docs.oracle.com/javase%2F7%2Fdocs%2Fapi%2F%2F/java/util/TreeSet.html) class, created because C#'s native [`SortedSet<T>`](https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic.sortedset-1?view=net-8.0) lacks key trawling and searching methods.

# Type parameters
- `T`: The type of elements stored in the set.

# Constructors
This class contains six constructor overloads:

- `()`
- `(IComparer<T>)`
- `(Comparison<T>)`
- `(IEnumerable<T>)`
- `(IEnumerable<T>, IComparer<T>)`
- `(IEnumerable<T>, Comparison<T>)`

The parameters of these constructors are as follows:

- `IEnumerable<T>` **`elems`**: The elements with which to pre-populate the set. Overloads that don't have this parameter create an empty `AVLTreeSet`.
- `IComparer<T>` **`comparer`** *or* `Comparison<T>` **`comparer`**: The comparer or function that compares the elements of this set. Overloads that don't have either of these parameters use `T`'s naturel comparer, and throw an `InvalidOperationException` if `T` isn't naturally comparable.

# Properties
## `Count`
`int` - Gets the number of elements in this `AVLTreeSet<T>`.

## `IsReadOnly`
`bool` - Gets whether or not this `AVLTreeSet<T>` is read-only (which is always `false`).

# Methods

## Empty check
The `IsEmpty()` method simply returns `true` iff the `AVLTreeSet<T>` contains no elements, and `false` otherwise.

## Nearby items
The `SearchAround(T)` method takes any value `T` for the parameter **`value`**, and returns a `NodeTriplet<T>` with the requested value, the next-lower entry in the set, and the next-higher entry in the set (if the `AVLTreeSet<T>` contains them, respectively).

## Navigation
Through the `INavigableSet<T>` interface, `AVLTreeSet<T>` implements several methods for getting values higher or lower than a given value.

For all of these methods:
- "lowest" refers to the lowest value in the set.
- "lower" refers to the highest value *less than* the given value.
- "floor" refers to the highest value *less than or equal to* the given value.
- "ceiling" refers to the lowest value *greater than or equal to* the given value.
- "higher" refers to the lowest value *greater than* the given value.
- "highest" refers to the highest value in the set.
- "a relative value" just refers to whichever of those is applicable to the particular methods in question.

### Contains relative value
The methods `ContainsLower`, `ContainsFloor`, `ContainsCeiling`, and `ContainsHigher` are all `bool`s.

These methods all have one parameter, `T` **`from`**, which is the value relative to which another should be found.

They return `true` iff such a relative value exists, and `false` otherwise.

### Try get relative value
The methods `TryGetLower`, `TryGetFloor`, `TryGetCeiling`, and `TryGetHigher` are all `bool`s.

These methods have two parameters:
- `T` **`from`** - The value relative to which another should be found.
- `out T` **`value`** - When the method returns `true`, this contains the found value. When the method returns `false`, this contains `default(T)`.

They return `true` iff such a relative value exists, as well as setting `value` to that value, and `false` otherwise.

### Get relative value
The methods `Lower`, `Floor`, `Ceiling`, and `Higher` all directly get a relative value.

All of these methods have one parameter, `T` **`from`**, which is the value relative to which another should be found.

They return a `T` which is that relative value.

If the relative value doesn't exist, these methods throw an exception:
- `InvalidOperationException`: If the `AVLTreeSet<T>` is empty.
- `ArgumentOutOfRangeException`: If there is no such relative value.

### Get bounding values
The methods `LowestValue` and `HighestValue` return the bounding values of the set.

Both of these methods are parameterless, and return a `T` which is that bounding entry.

If the `AVLTreeSet<T>` is empty, an `InvalidOperationException` is thrown.

### Google Code methods
These methods were included with the original entry on Google Code:
- `bool Delete(T arg)` - If the `AVLTreeSet<T>` contains `arg`, removes it from the set and returns `true`. Otherwise, returns `false`.
- `bool DeleteMax()` - If the `AVLTreeSet<T>` contains any values, removes the lowest one and returns `true`. Otherwise, returns `false`.
- `bool DeleteMin()` - If the `AVLTreeSet<T>` contains any values, removes the highest one and returns `true`. Otherwise, returns `false`.
- `int GetHeightLogN()` - Returns the height of the tree.
- `bool GetMax(out T value)` - If the `AVLTreeSet<T>` contains any values, sets `value` to the highest value and returns `true`. Otherwise, sets `value` to `default(T)` and returns false.
- `bool GetMin(out T value)` - If the `AVLTreeSet<T>` contains any values, sets `value` to the lowest value and returns `true`. Otherwise, sets `value` to `default(T)` and returns false.
- `void Print()` - Writes this instance's data using `Console.Write` and `Console.WriteLine`.
- `void ReplaceValue(T from, T to)` - If the `AVLTreeSet<T>` contains `from`, replaces it with `to`. Throws an `InvalidOperationException` if the `AVLTreeSet<T>` doesn't contain `from`, or an `ArgumentOutOfRangeException` if `to` is lower than `Lower(from)` or higher than `Higher(from)`.

### Standard Set methods
These behave in a similar manner to other `ISet<T>` implementations and will just be summarized here:
- `bool Add(T arg)` - If `arg` isn't already in the set, adds it and returns `true`. Otherwise, returns `false`.
- `void ICollection<T>.Add(T arg)` - If `arg` isn't already in the set, adds it. Otherwise, does nothing.
- `void Clear()` - Clears the `AVLTreeSet<T>`.
- `bool Contains(T arg)` - Returns `true` iff the `AVLTreeSet<T>` contains `arg` and `false` otherwise.
- `void CopyTo(T[] array, int index)` - Copes the elements of the `AVLTreeSet<T>` into an array.
- `void ExceptWith(IEnumerable<T> elems)` - Removes all elements from the `AVLTreeSet<T>` that are also in `elems`.
- `IEnumerator<T> GetEnumerator()` - Gets an enumerator over the elements of the `AVLTreeSet<T>`.
- `IEnumerator IEnumerable.GetEnumerator()` - Gets a typeless enumerator over the elements of the `AVLTreeSet<T>`.
- `void IntersectWith(IEnumerable<T> elems)` - Removes all elements from the `AVLTreeSet<T>` that are not also in `elems`.
- `bool IsProperSubsetOf(IEnumerable<T> other)` - Returns true iff this `AVLTreeSet<T>` is a proper subset of `other`; that is, all elements of this set are also in `other`, and there are some elements of `other` that are not in this set.
- `bool IsProperSupersetOf(IEnumerable<T> other)` - Returns true iff this `AVLTreeSet<T>` is a proper superset of `other`; that is, all elements of `other` are also in this set, and there are some elements of this set that are not in `other`.
- `bool IsSubsetOf(IEnumerable<T> other)` - Returns true iff this `AVLTreeSet<T>` is a subset of `other`; that is, all elements of this set are also in `other`.
- `bool IsSupersetOf(IEnumerable<T> other)` - Returns true iff this `AVLTreeSet<T>` is a superset of `other`; that is, all elements of `other` are also in this set.
- `bool Overlaps(IEnumerable<T> other)` - Returns true iff this `AVLTreeSet<T>` overlaps `other`; that is, the two sets have any elements in common.
- `bool Remove(T item)` - If `item` is part of this `AVLTreeSet<T>`, removes it and returns `true`. Otherwise, returns `false`.
- `bool SetEquals(IEnumerable<T> other)` - Returns `true` iff this `AVLTreeSet<T>` contains exactly the same set of items as `other`. Otherwise, returns `false`.
- `void SymmetricExceptWith(IEnumerable<T> elems)` - Removes all elements from this `AVLTreeSet<T>` that are in `elems`, and adds all elements from `elems` that are not in this `AVLTreeSet<T>`.
- `void UnionWith(IEnumerable<T> elems)` - Adds all elements from `elems` to this `AVLTreeSet<T>` that are not already in it.
