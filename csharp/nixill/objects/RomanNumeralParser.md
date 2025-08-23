---
layout: page
title: RomanNumeralParser class (Nixill.Objects)
permalink: /csharp/nixill/objects/RomanNumeralParser
---

A class that provides parsing methods for Roman numeral strings.

The parser only works for integers and uses the symbols `-_MDCLXVI`. `_` is used as a thousands separator to allow for any arbitrarily long integer to be parsed.

`public class RomanNumeralParser`

# Constructors
There is only one constructor.

Parameters:
- `RomanNumeralRules` **`rules`** - The ruleset to use for converting numbers to Roman numerals (re: subtraction).

# Methods
## `ToRoman(long)`
`string` - Converts a number to Roman numerals using the provided subtraction rules.

Parameters:
- `long` **`input`** - The number to convert.

Return: The number expressed in Roman numerals.

# Static Methods
## `ToLong(string)`
`long` - Converts Roman numerals to a numeric type. Since subtraction rules don't apply, this is a static method.

Parameters:
- `string` **`input`** - The string to convert.

Return: The number as a numeric data type.
