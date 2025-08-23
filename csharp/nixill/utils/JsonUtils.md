---
layout: page
title: EnumerableUtils class (Nixill.Utils)
permalink: /csharp/nixill/utils/JsonUtils
---

Utilities and extension methods for working with JsonNodes.

`public static class JsonUtils`

# Extension methods
## `JsonNode.ReadPath(params object[])`
`JsonNode` - Reads a JSON element down a specified path from another element.

Parameters:
- `this JsonNode` **`root`** - The root to start searching from.
- `params object[]` **`pathElements`** - Path elements to find one at a time.

Returns: The JSON node at the given path, or null if the path is not found at any point.

Example:
```cs
// The "obj" variable is the following JSON object:
// {
//   "first": [
//     { "second": 35 },
//     { "second": 15 }
//   ]
// }
Console.WriteLine(obj.ReadPath("first", 1, "second")); // returns 15
```

## `JsonNode.WritePath(JsonNode, params object[])`
`void` - Writes a JSON element down a specified path from another element, creating other elements as necessary

Parameters:
- `this JsonNode` **`root`** - The root to start searching from.
- `JsonNode` **`value`** - The value to write at the end of the path.
- `params object[]` **`pathElements`** - Path elements to find one at a time.

Example:
```cs
// The "obj" variable is an empty JSON object ({}).
obj.WritePath(true, "test", "of", "path"); // returns 15
// The "obj" variable is now the following JSON object:
// {
//   "test": {
//     "of": {
//       "path": true
//     }
//   }
// }
```