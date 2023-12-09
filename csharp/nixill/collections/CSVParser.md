---
layout: page
title: CSVParser class (Nixill.Collections.Grid.CSV)
permalink: /csharp/nixill/collections/CSVParser
---

This class contains static methods to convert between Grids of strings and comma separated value format files and text.

The parser follows the specifications laid out in [RFC 4180](https://tools.ietf.org/html/rfc4180), with the following exceptions:

- Input records may be separated by CRLF, CR, or LF (but not LFCR).
- Output records are separated by LF, not CRLF.
- In input, two consecutive double quotes always produces a double quote character, even when not enclosed in quotes.

# Methods
## `CSVEscape(input)`
`string` - Returns a single string, escaped to be one CSV value.

If the input string contains any quotes (`"`), carriage returns (`\r`), linefeeds (`\n`), or commas (`,`), all quotes within the string are doubled and the string gets wrapped in quotes. Otherwise, the input string is r eturned unaltered.

Parameters:
- `string` **`input`** - The string to escape.

Returns: The input string, altered or not altered as described above.

## `EnumerableToGrid(IEnumerable<char>)`
`Grid<string>` - Reads a char enumerator and converts the enumerated chars into a Grid of strings.

Parameters:
- `IEnumerable<char>` **`input`** - The enumerable object to read.

Returns: The parsed Grid of strings.

## `EnumerableToRows(IEnumerable<char>)`
`IEnumerable<IList<string>>` - Reads a char enumerator and converts the enumerated chars into an enumerable of grid rows.

Parameters:
- `IEnumerable<char>` **`input`** - The enumerable object to read.

Returns: An enumerator over the rows of the Grid.

## `FileToGrid(string)`
`Grid<string>` - Reads a CSV file into a Grid of strings.

Parameters:
- `string` **`path`** - The path of the file to read.

Returns: The generated `Grid<string>`.

## `GridToFile<T>(IGrid<T>)`
`void` - Converts a grid to a CSV string and writes it to a file.

Type parameters:
- `T` - The type of objects contained in the Grid being stringed.

Parameters:
- `IGrid<T>` **`input`** - The grid to convert to CSV.
- `string` **`file`** - The file to write to.

## `GridToString<T>(IGrid<T>)`
`string` - Returns a string containing the CSV representation of a Grid.

Type parameters:
- `T` - The type of objects contained in the Grid being stringed.

Parameters:
- `IGrid<T>` **`input`** - The grid to convert to CSV.

Returns: The aforementioned string.

## `GridToStringEnumerable<T>(IGrid<T>)`
Returns an enumerator over each row as a grid of strings.

The strings returned by the enumerator this method returns are one row of the grid each - however, it is not guaranteed that such strings are only one line. There may be multiple lines due to grid elements with linebreaks.

Type parameters:
- `T` - The type of objects contained in the Grid being stringed.

Parameters:
- `IGrid<T>` **`input`** - The grid to convert to CSV.

Returns: An enumerator over the rows of the CSV.

## `StreamToGrid(StreamReader)`
`Grid<string>` - Reads a CSV stream into a Grid of strings.

Parameters:
- `StreamReader` **`reader`** - The StreamReader to read from.

Returns: The generated `Grid<string>`.

## `StringToGrid(string)`
`Grid<string>` - Reads a CSV string into a Grid of strings.

Parameters:
- `string` **`input`** - The input to read.

