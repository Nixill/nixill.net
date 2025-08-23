---
layout: page
title: Cipher class (Nixill.Objects)
permalink: /csharp/nixill/objects/Cipher
---

A simple one-way substitution cipher.

Instances of the Cipher class can be used for multi-character substitutions including swaps and cycles.

`public class Cipher`

# Constructors
There is only one constructor overload, which creates a new Cipher.

The two parameters should be the same length. For each position `i` in the strings, the character `src[i]` becomes the character `trg[i]` when the Cipher is applied.

Parameters:
- `string` **`src`** - The characters that are converted from.
- `string` **`trg`** - The characters that are converted to.

# Properties
## `Reverse`
`Cipher` - Gets the reverse of this Cipher, which is the same as this Cipher but with its Source and Target strings swapped.

## `Reversible`
`bool` - Gets whether or not the Cipher is reversible.

A Cipher is said to be Reversible iff all of the following apply:
- Every Source character maps to exactly one Target character.
- Every Target character has exactly one Source character mapped to it.
- Every Target character is also a Source character.
- No Source character maps to null.

## `Source`
`string` - Gets the source string of the Cipher.

## `Target`
`string` - Gets the target string of the Cipher.

# Methods
## `Apply(string)`
`string` - Applies the Cipher to a string. Within the input string, any character matching a character in the source string is replaced with a character in the same position in the target string.

Parameters:
- `string` **`input`** - The string to cipher.

Returns: The ciphered string.