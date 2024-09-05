# Basic Syntax

## Package definition and imports

Package specification should be at the top of the source file

```kotlin
package my.demo

import kotlin.text.*

// ...
```

A source file may start with a package declaration:

```kotlin
package org.example

fun printMessage() { /*...*/ }
class Message { /*...*/ }

// ...
```

the full name of `printMessage()` is `org.example.printMessage`, and the full name of `Message` is `org.example.Message`.

## Default imports

A number of packages are imported into every Kotlin file by default:

- `kotlin.*`
  Core functions and types, available on all supported platforms.
- `kotlin.annotation.*`
  Library support for the Kotlin annotation facility.
- `kotlin.collections.*`
  Collection types, such as **Iterable**, **Collection**, **List**, **Set**, **Map** and related top-level and extension functions.
- `kotlin.comparisons.*`
  Helper functions for creating **Comparator** instances.
- `kotlin.io.*`
  IO API for working with files and streams.
- `kotlin.ranges.*`
  Ranges, Progressions and related top-level and extension functions.
- `kotlin.sequences.*`
  Sequence type that represents lazily evaluated collections. Top-level functions for instantiating sequences and extension functions for sequences.
- `kotlin.text.*`
  Functions for working with text and regular expressions.

## Additional packages are imported depending on the target platform:

JVM: - `java.lang.*` - `kotlin.jvm.*`
JS: - `kotlin.js.*`

## Imports

```kotlin
import org.example.Message // Message is now accessible without qualification
import org.example.* // everything in 'org.example' becomes accessible

import org.test.Message as TestMessage // TestMessage stands for 'org.test.Message'
```

you can also use `import` to import other declarations:

- top-level functions and properties
- functions and properties declared in object declarations
- enum constants
