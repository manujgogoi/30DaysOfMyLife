# Functions

A function with two `Int` parameters and `Int` return type:

```kotlin
fun sum(a: Int, b: Int): Int {
    return a + b;
}
```

A function body can be an expression. Its return type is inferred:

```kotlin
fun sum(a: Int, b: Int) = a + b;
```

A function that returns no meaningful value:

```kotlin
fun sum(a: Int, b: Int): Unit {
    println("Sum of $a and $b is ${a + b}")
}
```

`Unit` return type can be omitted:

```kotlin
fun sum (a: Int, b: Int) {
    println("Sum of $a and $b is ${a + b}")
}
```

## Default arguments

```kotlin
fun read (b: ByteArray, off: Int = 0, len: Int = b.size) {/* function body */}
```

## Overriding methods

Overriding methods always use the base method's default parameter values. When overriding a method that has default parameter values, the default parameter values must be omitted from the signature:

```kotlin
open class A {
    open fun foo(i: Int = 10) {/* function body */}
}

class B: A() {
    override fun foo(i: Int) {/* function body */} // No default value is allowed.
}
```

If a default parameter precedes a parameter with no default value, the default value can only be used by calling the function with named arguments:

```kotlin
fun foo(
    bar: Int = 0,
    baz: Int,
) { /*...*/ }

foo(baz = 1) // The default value bar = 0 is used
```

If the last argument after default parameters is a lambda, you can pass it either as a named argument or outside the parentheses:

```kotlin
fun foo (
    bar: Int = 0,
    baz: Int = 1,
    qux: () -> Unit,
) { /* function body */}

foo(1) { println("hello") }     // Uses the default value baz = 1
foo(qux = { println("hello") }) // Uses both default values bar = 0 and baz = 1
foo { println("hello") }        // Uses both default values bar = 0 and baz = 1
```

## Named arguments

```kotlin
fun reformat(
    str: String,
    normalizeCase: Boolean = true,
    upperCaseFirstLetter: Boolean = true,
    divideByCamelHumps: Boolean = false,
    wordSeparator: Char = ' ',
) { /*...*/ }
```

When calling this function, you don't have to name all its arguments:

```kotlin
reformat(
    "String!",
    false,
    upperCaseFirstLetter = false,
    divideByCamelHumps = true,
    '_'
)
```

You can skip all the ones with default values:

```kotlin
reformat("This is a long String!")
```

```kotlin
reformat("This is a short String!", upperCaseFirstLetter = false, wordSeparator = '_')
```

You can pass a variable number of arguments (`vararg`) with names using the spread operator:

```kotlin
fun foo(vararg strings: String) { /*...*/ }
foo(strings = *arrayOf("a", "b", "c"))
```

## Unit-returning functions

If a function does not return a useful value, its return type is Unit. Unit is a type with only one value - Unit. This value does not have to be returned explicitly:

```kotlin
fun printHello(name: String?): Unit {
    if (name != null)
        println("Hello $name")
    else
        println("Hi there!")
    // `return Unit` or `return` is optional
}
```

The `Unit` return type declaration is also optional. The above code is equivalent to:

```kotlin
fun printHello(name: String?) { ... }
```

## Variable number of arguments (varargs)

```kotlin
fun <T> asList (vararg ts: T): List<T> {
    val result = ArrayList<T>()
    for(t in ts) {
        result.add(t)
    }
    return result
}

val list = asList(1, 2, 3)

val a = arrayOf(1, 2, 3)
val list = asList(-1, 0, *a, 4) /* spread operator (prefix the array with *) */
```

```kotlin
val a = intArrayOf(1, 2, 3) // IntArray is a primitive type array
val list = asList(-1, 0, *a.toTypedArray(), 4)
```

## Generic functions

Functions can have generic parameters, which are specified using angle brackets before the function name:

```kotlin
fun <T> singletonList(item: T): List<T> { /*...*/ }
```
