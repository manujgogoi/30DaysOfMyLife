## Define and use Functions

```kotlin
fun main() {
    birthdayGreeting()
}

fun birthdayGreeting() {
    println("Happy Birthday, Rover!")
    println("You are now 5 years old!")
}
```

## Return a value from a function

1. the `Unit` type

```kotlin
fun main() {
    birthdayGreeting()
}

fun birthdayGreeting(): Unit {
    println("Happy Birthday, Rover!")
    println("You are now 5 years old!")
}
```

> It's optional to specify the Unit return type in Kotlin. For functions that don't return anything, or returning Unit, you don't need a return statement.

```kotlin
fun main() {
    val greeting = birthdayGreeting()
    println(greeting)
}

fun birthdayGreeting(): String {
    val nameGreeting = "Happy Birthday, Rover!"
    val ageGreeting = "You are now 5 years old!"
    return "$nameGreeting\n$ageGreeting"
}
```

## Add a parameter to a function

```kotlin
fun birthdayGreeting(name: String): String {
    val nameGreeting = "Happy Birthday, $name!"
    val ageGreeting = "You are now 5 years old!"
    return "$nameGreeting\n$ageGreeting"
}
```

```kotlin
fun birthdayGreeting(name: String, age: Int): String {
    val nameGreeting = "Happy Birthday, $name!"
    val ageGreeting = "You are now $age years old!"
    return "$nameGreeting\n$ageGreeting"
}
```

```kotlin
fun main() {
    println(birthdayGreeting("Rover", 5))
    println(birthdayGreeting("Rex", 2))

    // Named Arguments
    println(birthdayGreeting(name = "Rex", age = 2))

    // Named Arguments in a different order
    println(birthdayGreeting(age = 2, name = "Rex"))
}
```

## Default Arguments

```kotlin
fun birthdayGreeting(name: String = "Rover", age: Int): String {
    return "Happy Birthday, $name! You are now $age years old!"
}

println(birthdayGreeting(age = 5))
println(birthdayGreeting("Rex", 2))
```
