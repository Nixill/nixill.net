---
layout: page
title: RomanNumeralRules class (Nixill.Objects)
permalink: /csharp/nixill/objects/RomanNumeralRules
---

A set of rules for converting integers to Roman numerals. These rules govern how subtraction is used instead of always using addition.

For rules not specified, the default values are:

| Value | Numerals |
| :---- | :------- |
| 0     |          |
| 1     | I        |
| 2     | II       |
| 3     | III      |
| 4     | IIII     |
| 5     | V        |
| 10    | X        |
| 20    | XX       |
| 30    | XXX      |
| 40    | XXXX     |
| 50    | L        |
| 100   | C        |
| 200   | CC       |
| 300   | CCC      |
| 400   | CCCC     |
| 500   | D        |

# Example
To create a tighter mapping for numerals than the commonly seen subtraction rules:

```csharp
RomanNumeralRules tightRules = new RomanNumeralRules()
{
  [4] = "IV",
  [9] = "IX",
  [40] = "XL",
  [49] = "IL",
  [90] = "XC",
  [99] = "IC",
  [400] = "CD",
  [490] = "XD",
  [499] = "ID",
  [900] = "CM",
  [990] = "XM",
  [999] = "IM"
}

RomanNumeralParser parser = new RomanNumeralParser(tightRules);

Console.WriteLine(parser.ToRoman(498)); // XDVIII (as opposed to the COMMON ruleset's CDXCVIII, or the NONE ruleset's CCCCLXXXXVIII)
```

# Constructors
RomanNumeralRules has only one constructor, `RomanNumeralRules(IDictionary<int, string>)`, which creates a set of RomanNumeralRules using the specified input.

Parameters
- `IDictionary<int, string>` **`rules`** - The rules to use.

# Static fields
## `COMMON`
`readonly RomanNumeralRules` - The common set of Roman numeral writing rules, which contains the following mappings that overwrite defaults:

| Value | Numerals |
| :---- | :------- |
| 4     | IV       |
| 9     | IX       |
| 40    | XL       |
| 90    | XC       |
| 400   | CD       |
| 900   | CM       |

## `NONE`
`readonly RomanNumeralRules` - An empty set of Roman numeral writing rules, containing no values that overwrite defaults.

# Methods
## `RuleFor(int)`
`(int, string)` - Get the first applicable rule to a number.

## Parameters
- `int` **`val`** - The value to get, which must be between 0 and 999 inclusive.

## Returns
Tuple of:
- `int` - The exact value to which the string applies. Can be subtracted from the input and re-run to get the next rule.
- `string` - The string for the rule. When inputs are chained as described above, all strings can be concatenated to get the original number in Roman numerals.

## Exceptions
- `ArgumentOutOfRangeException`: If `val` is less than `0` or greater than `999`.