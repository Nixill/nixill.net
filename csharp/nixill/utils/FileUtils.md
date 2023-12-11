---
layout: page
title: FileUtils class (Nixill.Utils)
permalink: /csharp/nixill/utils/FileUtils
---

Utilities for working with files.

`public class FileUtils`

# Static methods
## `FileCharEnumerator(string)`
`IEnumerable<char>` - An enumerable over characters within a file.

Parameters:
- `string` **`path`** - The path of the file to read.

Returns: An enumerable over the characters within a file.

## `StreamCharEnumerator(string)`
`IEnumerable<char>` - An enumerable over characters from a stream.

Parameters:
- `StreamReader` **`reader`** - The stream to read.

Returns: An enumerable over the characters from the stream.
