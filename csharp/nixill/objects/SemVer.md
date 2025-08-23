---
layout: page
title: SemVer class (Nixill.Objects)
permalink: /csharp/nixill/objects/SemVer
---

Represents a [semver 2.0.0](https://semver.org/) compatible semantic version.

# Constructors
The following constructor overloads are available:

- `SemVer(int major, int minor, int patch)`
- `SemVer(int major, int minor, int patch, string prerelease, string build)`

In both of the above, `major`, `minor`, and `patch` must be non-negative integers; `prerelease` and `build` must be null if omitted or otherwise follow their specifications in rules 9 and 10.

- `SemVer(string version)`

This overload allows specifying the version as a string, which must follow a semantic version string's rules.

# Fields
## `BuildMetadata`
`readonly string` - The build metadata ("237ab549spec1812" of "1.23.456+237ab549spec1812"), as defined by spec rule 10.

## `Major`
`readonly int` - The major version number ("1" of "1.23.456"), as defined by spec rule 8.

## `Minor`
`readonly int` - The minor version number ("23" of "1.23.456"), as defined by spec rule 7.

## `Patch`
`readonly int` - The patch number ("456" of "1.23.456"), as defined by spec rule 6.

## `PreRelease`
`readonly string` - The prerelease identifiers ("beta" of "1.23.456-beta"), as defined by spec rule 9.

# Methods
## `BumpMajor()`
`SemVer` - Creates a new SemVer representing the next major release after this one, incremented according to spec rule 8.

Returns: The copied SemVer.

## `BumpMinor()`
`SemVer` - Creates a new SemVer representing the next minor release after this one, incremented according to spec rule 7.

Returns: The copied SemVer.

## `BumpPatch()`
`SemVer` - Creates a new SemVer representing the next patch release after this one, incremented according to spec rule 6.

Returns: The copied SemVer.

## `CompareTo(SemVer)`
`int` - Compares this SemVer to another, following spec rule 11.

Parameters:
- `SemVer` **`target`** - The SemVer to which this one should be compared.

Returns: An int that is negative if `this` represents an older version than `target`, 0 if `this` and `target` represent the same version, and positive if `this` represents a newer version than `target`.

## `Equals(object)`
`bool` - Compares this SemVer to another.

This check follows spec rule 11. Notably, this means that build metadata is ignored for the purposes of the check. Use `EqualsStrict()` to include build metadata.

Parameters:
- `object` **`obj`** - The other object to which this should be compared. Should be a `SemVer`.

Returns: `true` iff the two SemVers are equal; `false` otherwise.

Exceptions:
- `InvalidCastException`: `obj` is not a `SemVer`.

## `EqualsStrict(SemVer)`
`bool` - Compares this SemVer to another.

This check does not follow spec rule 11. Instead, build metadata is included in this check. Use `Equals()` to exclude build metadata and follow rule 11.

Parameters:
- `SemVer` **`target`** - The other SemVer to which this should be compared.

Returns: `true` iff the two SemVers are equal; `false` otherwise.

## `GetHashCode()`
`int` - Gets the hash code of this SemVer.

Since `Equals()` follows rule 11, this function also ignores the build metadata, to comply with the contract between `Equals` and `GetHashCode`.

Returns: A hash code for this SemVer.

## `Release()`
`SemVer` - Creates a copy of this SemVer with no pre-release tag or build metadata.

Returns: The copied SemVer.

## `ToString()`
`string` - Converts the SemVer to a string.

Returns: The string representation of the SemVer.

## `WithBuildMetadata(string)`
`SemVer` - Returns a new copy of this SemVer with the specified build metadata tag, leaving the other fields unchanged.

Parameters:
- `int` **`build`** - The build metadata to use. Specify `null` to remove the build metadata tag.

Returns: The adjusted SemVer.

## `WithMajor(int)`
`SemVer` - Returns a new copy of this SemVer with the specified major version number, leaving the other fields unchanged.

Parameters:
- `int` **`maj`** - The major version to use.

Returns: The adjusted SemVer.

## `WithMinor(int)`
`SemVer` - Returns a new copy of this SemVer with the specified minor version number, leaving the other fields unchanged.

Parameters:
- `int` **`min`** - The minor version to use.

Returns: The adjusted SemVer.

## `WithPatch(int)`
`SemVer` - Returns a new copy of this SemVer with the specified patch number, leaving the other fields unchanged.

Parameters:
- `int` **`pat`** - The patch to use.

Returns: The adjusted SemVer.

## `WithPreRelease(string)`
`SemVer` - Returns a new copy of this SemVer with the specified pre-release tag, leaving the other fields unchanged.

Parameters:
- `string` **`pr`** - The pre-release tag to use. Specify `null` to remove the pre-release tag.

Returns: The adjusted SemVer.

# Operators
## Binary operators
- (`bool`) `SemVer left == SemVer right` - Returns true iff `left` and `right` represent the same version, ignoring the build metadata.
- (`bool`) `SemVer left != SemVer right` - Returns true iff `left` and `right` represent different versions, ignoring the build metadata.
- (`bool`) `SemVer left < SemVer right` - Returns true iff `left` represents an earlier version than `right`.
- (`bool`) `SemVer left <= SemVer right` - Returns true iff `left` represents an earlier version than `right`, or the same version.
- (`bool`) `SemVer left > SemVer right` - Returns true iff `left` represents a later version than `right`.
- (`bool`) `SemVer left >= SemVer right` - Returns true iff `left` represents a later version than `right`, or the same version.

