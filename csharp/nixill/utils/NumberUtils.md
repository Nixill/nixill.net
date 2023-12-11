---
layout: page
title: NumberUtils class (Nixill.Utils)
permalink: /csharp/nixill/utils/NumberUtils
---

Provides utilities for working with or converting numbers.

`public class NumberUtils`

# Static methods
## `CharToInt(chr)`
`int` - Converts a character, which is a digit in any base of greater value than that digit, to its base 10 int value.

This method doesn't take a `base` parameter because the base doesn't alter the value of the digit. For example, `c` has value 12 whether it's expressed in base 13 or 33.

Parameters:
- `char` **`chr`** - The character to convert.

Returns: The character as converted.

## `HasAllBits(int, int)`
`bool` - Returns true iff the source number has all of the target bits.

Specifically, returns `src & trg == trg`.

Special case: If `trg` is 0, returns `src == 0`.

Parameters:
- `int` **`src`** - The source number
- `int` **`trg`** - The target number

Returns: See above.

## `HasAnyBits(int, int)`
`bool` - Returns true iff the source number has any of the target bits.

Specifically, returns `src & trg != 0`.

Special case: If `trg` is 0, returns `src != 0`.

Parameters:
- `int` **`src`** - The source number
- `int` **`trg`** - The target number

Returns: See above.

## `IntToChar(int)`
`char` - Converts an integer to a character representing a digit of the given value in any higher base.

This method doesn't take a `base` parameter because the base doesn't alter the value of the digit. For example, `c` has value 12 whether it's expressed in base 13 or 33.

Parameters:
- `int` **`i`** - The integer to convert.

Returns: The integer as converted.

## `IntToLeadingZeroString(int, int)`
`string` - Converts an int to a bijective number.

A bijective number is a sequence in which numbers which start with zero are distinct from numbers which do not. For example, base 10
would count as follows: `0, 1, 2, ..., 9, 00, 01, ..., 09, 10, 11, ..., 99, 000, 001, ...`

For bijective numbers, base 1 is a valid base (`0, 00, 000, ...`). The highest valid base is 36.

This method was already named IntToLeadingZeroString when I found out about the term "bijective number", and thus kept that name for compatibility.

Parameters:
- `int` **`input`** - The int which should be converted.
- `int` **`bs`** - The base to which to convert the number (between 1 and 36).

Returns: The number as converted.

## `IntToString(int, int)`
`string` - Converts an int to a string in an arbitrary base.

Parameters:
- `int` **`input`** - The int which should be converted.
- `int` **`bs`** - The base to which to convert the number (between 2 and 36).

Returns: The number as converted.

## `LeadingZeroStringToInt(string, int)`
`int` - Converts a bijective number to an int.

See `IntToLeadingZeroString()` above for information on bijective numbers.

This method was already named LeadingZeroStringToInt when I found out about the term "bijective number", and thus kept that name for compatibility.

Parameters:
- `string` **`input`** - The string which should be converted.
- `int` **`bs`** - The base from which to convert the number (between 1 and 36).

Returns: The number as converted.

## `NNMod`
Returns the non-negative modulus of division of `n` by `d`.

Parameters:
- **`n`** - The numerator of this division.
- **`d`** - The denominator of this division.

Return: The modulus of dividing `n` by `d`. If either is negative, a positive modulus is still returned.

Overloads:
- `int NNMod(int, int)`
- `long NNMod(long, long)`
- `float NNMod(float, float)`
- `double NNMod(double, double)`
- `decimal NNMod(decimal, decimal)`

## `StringToInt(string, int)`
`int` - Converts a string in an arbitrary base to an int.

Parameters:
- `string` **`str`** - The string which should be converted.
- `int` **`bs`** - The base from which to convert the number (between 2 and 36).

Returns: The number as converted.
