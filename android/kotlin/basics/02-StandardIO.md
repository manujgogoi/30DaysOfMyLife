# Program entry point

```kotlin
fun main() {
    println("Hello World!");
}
```

Another form:

```kotlin
fun main (arg: Array<String>) {
    println(args.contentToString());
}
```

## Print to the standard output

```kotlin
print("Hello ")
print("world!")
```

`println` prints its arguments and adds a line break, so that the next thing you print appears on the next line:

```kotlin
println("Hello world!")
println(42)
```

## Read from the standard input

The `readln()` function reads from the standard input. This function reads the entire line the user enters as a string.

```kotlin
println("Enter any word: ")
val yourWord = readln()

print("You entered the word: ")
print(yourWord)
```
