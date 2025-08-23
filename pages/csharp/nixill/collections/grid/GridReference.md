---
layout: page
title: GridReference class (Nixill.Collections.Grid)
permalink: /csharp/nixill/collections/grid/GridReference
---

A class that maintains a two-dimensional coordinate as well as conversions of that coordinate to popular spreadsheet cell reference formats:

"A1" notation refers to a notation where a row is given as a 1-indexed number, and a column is given as a base-26 bijective numbering system with only letters as the digits. (A, B, C … Y, Z, AA, AB … ZY, ZZ, AAA, AAB …)

"R1C1" notation refers to a notation that uses the literal letter R, then a 1-indexed row number, then the letter C, then a 1-indexed column number.

While GridReferences themselves support negative indices (for grid types that support them), neither of the string formats support conversion to or from negative indices. Additionally, conversion to or from strings will convert 1-indexed references like `B4` into 0-indexed int references such as `(1, 3)`.

`public class GridReference : IComparable<GridReference>`

# Constructors
There are two constructor overloads.

## `GridReference(int, int)`
Constructs a new GridReference given its individual components.

Parameters:
- `int` **`col`** - The column to use for this reference.
- `int` **`row`** - The row to use for this reference.

## `GridReference(string)`
Constructs a new GridReference given a string representation thereof.

This constructor accepts A1 or R1C1 notations as described above.

Parameters:
- `int` **`input`** - The input to use.

# Properties
## `Column`
`int` - Gets the column number of the GridReference.

## `Row`
`int` - Gets the row number of the GridReference.

## `Transposed`
`GridReference` - Returns a copy of this GridReference with its components swapped.

# Methods
## `CompareTo(GridReference)`
`int` - Compares this GridReference to another, and returns:

- A negative number if `this < other`.
- 0 if `this == other`.
- A positive number if `this > other`.

Rows are compared before columns; therefore `this` is "less than" `other` if either of the following are true:
- `this` is a lower-numbered row than `other`.
- `this` is the same row as `other`, but is a lower-numbered column.

Parameters:
- `GridReference` **`other`** - The other grid reference for comparison.

Returns: An integer as described above.

## `Equals(object)`
`bool` - Returns true iff the other object is a GridReference with the same Row and Column.

If the other object is not a GridReference, this returns false.

Parameters:
- `object` **`obj`** - The object to compare for equality.

Returns: `true` iff `obj` is a GridReference and has the same Row and Column as `this`.

## `GetHashCode()`
`int` - Returns a hash code for this GridReference.

In particular, this returns an int whose high 16 bits are the low 16 bits of the row number, and whose low 16 bits are the low 16 bits of the column number.

Returns: This GridReference's hash code.

## `ToA1String()`
`string` - Returns a string representation of this GridReference in A1 notation, as described above.

Returns: The aforementioned string.

## `ToR1C1String()`
`string` - Returns a string representation of this GridReference in R1C1 notation, as described above.

Returns: The aforementioned string.

## `ToString()`
See `ToA1String()` above.

# Static methods
## `ColumnNameToNumber(string)`
Changes a column name in A1 notation (described above) to a zero-indexed column number. For example, A becomes 0, B becomes 1, Z becomes 25, AA becomes 26, AB becomes 27, AZ becomes 51, BA becomes 52, and so on.

Parameters:
- `string` **`name`** - The name to convert.

Returns: The column number.

## `ColumnNumberToName(int)`
Changes a zero-indexed column number to a name in A1 notation (described above). For example, 0 becomes A, 1 becomes B, 25 becomes Z, 26 becomes AA, 27 becomes AB, 51 becomes AZ, 52 becomes BA, and so on.

Parameters:
- `int` **`number`** - The number to convert.

Returns: The column name.

# Operators
Explicit conversion operators:
- From `string` - Converts an A1 or R1C1 string into a GridReference.
- From `(int, int)` - Converts a two-int tuple (Column, Row) into a GridReference.

Implicit conversion operators:
- To `string` - Converts a GridReference into an A1 notation string.
- To `(int, int)` - Converts a GridReference into a two-int tuple (Column, Row).

Binary operators:
- `GridReference left == GridReference right` - Returns true iff two GridReferences are equal, as determined by `left.Equals(right)`.
- `GridReference left != GridReference right` - Returns true iff two GridReferences are not equal, as determined by `left.Equals(right)`.
- `GridReference left < GridReference right` - Returns true iff the left GridReference is less than or equal to the right, as determined by `left.CompareTo(right)`.
- `GridReference left <= GridReference right` - Returns true iff the left GridReference is less than the right, as determined by `left.CompareTo(right)`.
- `GridReference left > GridReference right` - Returns true iff the left GridReference is greater than or equal to the right, as determined by `left.CompareTo(right)`.
- `GridReference left >= GridReference right` - Returns true iff the left GridReference is greater than the right, as determined by `left.CompareTo(right)`.