# Kotlin Programming Guide: From Beginner to Advanced

## Introduction

Kotlin is a modern, statically-typed programming language that runs on the Java Virtual Machine (JVM) and can also be compiled to JavaScript or native code. Developed by JetBrains and officially supported by Google for Android development, Kotlin combines object-oriented and functional programming features. This guide provides a structured path from fundamental concepts to advanced techniques, preparing you to write production-ready Kotlin applications.

## Chapter 1: Getting Started

### Setting Up the Development Environment

To begin Kotlin development, install IntelliJ IDEA Community Edition or Android Studio. Both IDEs provide excellent Kotlin support with intelligent code completion, refactoring tools, and debugging capabilities.

Create a new Kotlin project:
1. Open IntelliJ IDEA
2. Select "New Project"
3. Choose "Kotlin" and "JVM" as the project template
4. Select Gradle with Kotlin DSL as the build system
5. Name your project and click "Finish"

### Your First Kotlin Program

Create a file named `Main.kt`:

```kotlin
fun main() {
    println("Hello, Kotlin!")
}
```

The `main` function serves as the entry point. Unlike Java, Kotlin does not require a class wrapper for the main function. The `println` function outputs text to the console followed by a newline.

### Exercise 1.1: Basic Output

Write a program that prints your name, age, and city on separate lines. Experiment with different text and formatting.

```kotlin
fun main() {
    println("Name: Alice")
    println("Age: 25")
    println("City: Berlin")
}
```

## Chapter 2: Variables and Data Types

### Declaring Variables

Kotlin provides two keywords for variable declaration:
- `val`: immutable (read-only) reference, similar to `final` in Java
- `var`: mutable reference that can be reassigned

```kotlin
val name: String = "Alice"  // Immutable
var age: Int = 25           // Mutable
age = 26                    // Valid
// name = "Bob"             // Error: Val cannot be reassigned
```

Kotlin uses type inference, allowing you to omit explicit types when the compiler can deduce them:

```kotlin
val city = "Frankfurt"      // Type inferred as String
var count = 0               // Type inferred as Int
```

### Basic Data Types

Kotlin treats everything as objects, with no primitive types:

```kotlin
val byte: Byte = 127
val short: Short = 32767
val int: Int = 2147483647
val long: Long = 9223372036854775807L

val float: Float = 3.14f
val double: Double = 3.14159265359

val boolean: Boolean = true
val char: Char = 'A'
val string: String = "Hello"
```

### Type Conversion

Kotlin requires explicit type conversions:

```kotlin
val intValue: Int = 42
val longValue: Long = intValue.toLong()
val doubleValue: Double = intValue.toDouble()
val stringValue: String = intValue.toString()
```

### String Templates

String templates provide embedded expressions:

```kotlin
val name = "Alice"
val age = 25
println("My name is $name and I am $age years old")
println("Next year I will be ${age + 1}")
```

### Exercise 2.1: Variable Practice

Create a program that calculates the area and perimeter of a rectangle. Store length and width as variables, compute the results, and display them using string templates.

```kotlin
fun main() {
    val length = 10.0
    val width = 5.0
    val area = length * width
    val perimeter = 2 * (length + width)

    println("Rectangle dimensions: $length x $width")
    println("Area: $area")
    println("Perimeter: $perimeter")
}
```

## Chapter 3: Operators and Expressions

### Arithmetic Operators

```kotlin
val a = 10
val b = 3

println(a + b)  // 13
println(a - b)  // 7
println(a * b)  // 30
println(a / b)  // 3 (integer division)
println(a % b)  // 1 (remainder)
```

### Comparison Operators

```kotlin
val x = 5
val y = 10

println(x == y)  // false
println(x != y)  // true
println(x < y)   // true
println(x > y)   // false
println(x <= y)  // true
println(x >= y)  // false
```

### Logical Operators

```kotlin
val a = true
val b = false

println(a && b)  // false (AND)
println(a || b)  // true (OR)
println(!a)      // false (NOT)
```

### Increment and Decrement

```kotlin
var count = 5
count++          // Post-increment: count becomes 6
count--          // Post-decrement: count becomes 5
++count          // Pre-increment: count becomes 6
--count          // Pre-decrement: count becomes 5
```

### Exercise 3.1: Calculator

Write a simple calculator that performs addition, subtraction, multiplication, and division on two numbers provided as variables.

```kotlin
fun main() {
    val num1 = 20.0
    val num2 = 4.0

    println("Addition: ${num1 + num2}")
    println("Subtraction: ${num1 - num2}")
    println("Multiplication: ${num1 * num2}")
    println("Division: ${num1 / num2}")
}
```

## Chapter 4: Control Flow

### If Expressions

In Kotlin, `if` is an expression that returns a value:

```kotlin
val max = if (a > b) a else b

val result = if (score >= 60) {
    "Pass"
} else {
    "Fail"
}
```

### When Expression

The `when` expression replaces switch statements and offers more flexibility:

```kotlin
val dayOfWeek = 3
val dayName = when (dayOfWeek) {
    1 -> "Monday"
    2 -> "Tuesday"
    3 -> "Wednesday"
    4 -> "Thursday"
    5 -> "Friday"
    6 -> "Saturday"
    7 -> "Sunday"
    else -> "Invalid day"
}

// With multiple conditions
when (x) {
    0, 1 -> println("x is 0 or 1")
    in 2..10 -> println("x is between 2 and 10")
    is String -> println("x is a String")
    else -> println("x is something else")
}
```

### For Loops

```kotlin
// Iterate over a range
for (i in 1..5) {
    println(i)  // 1, 2, 3, 4, 5
}

// Iterate with a step
for (i in 0..10 step 2) {
    println(i)  // 0, 2, 4, 6, 8, 10
}

// Iterate in reverse
for (i in 5 downTo 1) {
    println(i)  // 5, 4, 3, 2, 1
}

// Iterate over an array
val fruits = arrayOf("Apple", "Banana", "Cherry")
for (fruit in fruits) {
    println(fruit)
}

// Iterate with index
for ((index, fruit) in fruits.withIndex()) {
    println("$index: $fruit")
}
```

### While and Do-While Loops

```kotlin
// While loop
var count = 0
while (count < 5) {
    println(count)
    count++
}

// Do-while loop (executes at least once)
var number = 0
do {
    println(number)
    number++
} while (number < 5)
```

### Break and Continue

```kotlin
for (i in 1..10) {
    if (i == 5) break      // Exit loop
    if (i % 2 == 0) continue  // Skip even numbers
    println(i)
}
```

### Exercise 4.1: FizzBuzz

Implement the FizzBuzz problem: print numbers from 1 to 100, but for multiples of 3 print "Fizz", for multiples of 5 print "Buzz", and for multiples of both print "FizzBuzz".

```kotlin
fun main() {
    for (i in 1..100) {
        when {
            i % 15 == 0 -> println("FizzBuzz")
            i % 3 == 0 -> println("Fizz")
            i % 5 == 0 -> println("Buzz")
            else -> println(i)
        }
    }
}
```

## Chapter 5: Functions

### Basic Function Syntax

```kotlin
fun greet(name: String) {
    println("Hello, $name!")
}

fun add(a: Int, b: Int): Int {
    return a + b
}

// Single-expression function
fun multiply(a: Int, b: Int): Int = a * b

// Unit return type (void equivalent)
fun printSum(a: Int, b: Int): Unit {
    println(a + b)
}

// Unit can be omitted
fun printProduct(a: Int, b: Int) {
    println(a * b)
}
```

### Default Parameters

```kotlin
fun greet(name: String, greeting: String = "Hello") {
    println("$greeting, $name!")
}

greet("Alice")              // Hello, Alice!
greet("Bob", "Hi")          // Hi, Bob!
```

### Named Arguments

```kotlin
fun createUser(name: String, age: Int, city: String) {
    println("User: $name, $age, $city")
}

createUser(name = "Alice", age = 25, city = "Frankfurt")
createUser(age = 30, city = "Berlin", name = "Bob")
```

### Variable Number of Arguments (Varargs)

```kotlin
fun sum(vararg numbers: Int): Int {
    return numbers.sum()
}

println(sum(1, 2, 3))          // 6
println(sum(1, 2, 3, 4, 5))    // 15
```

### Higher-Order Functions

Functions that take functions as parameters or return functions:

```kotlin
fun operate(a: Int, b: Int, operation: (Int, Int) -> Int): Int {
    return operation(a, b)
}

val sum = operate(5, 3) { x, y -> x + y }      // 8
val product = operate(5, 3) { x, y -> x * y }  // 15
```

### Lambda Expressions

```kotlin
val square: (Int) -> Int = { x -> x * x }
println(square(5))  // 25

val greet: (String) -> Unit = { name -> 
    println("Hello, $name!")
}
greet("Alice")

// If lambda has single parameter, use 'it'
val double: (Int) -> Int = { it * 2 }
println(double(4))  // 8
```

### Exercise 5.1: Temperature Converter

Write functions to convert between Celsius and Fahrenheit. Use default parameters and single-expression syntax where appropriate.

```kotlin
fun celsiusToFahrenheit(celsius: Double): Double = celsius * 9/5 + 32

fun fahrenheitToCelsius(fahrenheit: Double): Double = (fahrenheit - 32) * 5/9

fun printTemperature(temp: Double, unit: String = "C") {
    when (unit.uppercase()) {
        "C" -> println("$temp°C = ${celsiusToFahrenheit(temp)}°F")
        "F" -> println("$temp°F = ${fahrenheitToCelsius(temp)}°C")
        else -> println("Unknown unit")
    }
}

fun main() {
    printTemperature(0.0)
    printTemperature(32.0, "F")
    printTemperature(100.0)
}
```

## Chapter 6: Collections

### Lists

```kotlin
// Immutable list
val fruits = listOf("Apple", "Banana", "Cherry")
println(fruits[0])           // Apple
println(fruits.size)         // 3
println(fruits.contains("Banana"))  // true

// Mutable list
val numbers = mutableListOf(1, 2, 3)
numbers.add(4)
numbers.remove(2)
numbers[0] = 10
println(numbers)  // [10, 3, 4]
```

### Sets

```kotlin
// Immutable set (no duplicates)
val uniqueNumbers = setOf(1, 2, 3, 2, 1)
println(uniqueNumbers)  // [1, 2, 3]

// Mutable set
val colors = mutableSetOf("Red", "Green", "Blue")
colors.add("Yellow")
colors.remove("Green")
println(colors)
```

### Maps

```kotlin
// Immutable map
val ages = mapOf("Alice" to 25, "Bob" to 30, "Charlie" to 35)
println(ages["Alice"])       // 25
println(ages.keys)           // [Alice, Bob, Charlie]
println(ages.values)         // [25, 30, 35]

// Mutable map
val scores = mutableMapOf("Math" to 90, "English" to 85)
scores["Science"] = 95
scores["Math"] = 92
println(scores)
```

### Collection Operations

```kotlin
val numbers = listOf(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

// Filter
val evenNumbers = numbers.filter { it % 2 == 0 }
println(evenNumbers)  // [2, 4, 6, 8, 10]

// Map
val squared = numbers.map { it * it }
println(squared)  // [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

// Reduce
val sum = numbers.reduce { acc, num -> acc + num }
println(sum)  // 55

// Find
val firstEven = numbers.find { it % 2 == 0 }
println(firstEven)  // 2

// Any, all, none
println(numbers.any { it > 5 })    // true
println(numbers.all { it > 0 })    // true
println(numbers.none { it < 0 })   // true

// Take and drop
println(numbers.take(3))       // [1, 2, 3]
println(numbers.drop(3))       // [4, 5, 6, 7, 8, 9, 10]

// Grouping
val grouped = numbers.groupBy { if (it % 2 == 0) "even" else "odd" }
println(grouped)  // {odd=[1, 3, 5, 7, 9], even=[2, 4, 6, 8, 10]}
```

### Exercise 6.1: Student Grade Analyzer

Create a program that manages student grades. Store student names and grades in a map, then calculate average, highest, and lowest grades. Filter students who passed (grade >= 60).

```kotlin
fun main() {
    val grades = mapOf(
        "Alice" to 85,
        "Bob" to 72,
        "Charlie" to 58,
        "Diana" to 94,
        "Eve" to 67
    )

    val average = grades.values.average()
    val highest = grades.maxByOrNull { it.value }
    val lowest = grades.minByOrNull { it.value }
    val passed = grades.filter { it.value >= 60 }

    println("Average grade: $average")
    println("Highest: ${highest?.key} with ${highest?.value}")
    println("Lowest: ${lowest?.key} with ${lowest?.value}")
    println("Students who passed: ${passed.keys}")
}
```

## Chapter 7: Null Safety

### Nullable Types

Kotlin's type system distinguishes between nullable and non-nullable references, preventing null pointer exceptions at compile time:

```kotlin
var name: String = "Alice"
// name = null  // Compilation error

var nullableName: String? = "Bob"
nullableName = null  // Valid
```

### Safe Call Operator

```kotlin
val length: Int? = nullableName?.length
println(length)  // null if nullableName is null

// Chain safe calls
val firstChar: Char? = nullableName?.uppercase()?.first()
```

### Elvis Operator

Provides a default value when the expression is null:

```kotlin
val name: String? = null
val displayName = name ?: "Unknown"
println(displayName)  // Unknown

val length = name?.length ?: 0
println(length)  // 0
```

### Not-Null Assertion Operator

Use with caution; throws exception if value is null:

```kotlin
val name: String? = "Alice"
val length: Int = name!!.length  // Use only when certain it's not null
```

### Safe Casts

```kotlin
val obj: Any = "Hello"
val str: String? = obj as? String  // Returns null if cast fails
val int: Int? = obj as? Int        // null
```

### Let Function

Execute code only if value is not null:

```kotlin
val name: String? = "Alice"
name?.let {
    println("Name length: ${it.length}")
    println("Uppercase: ${it.uppercase()}")
}
```

### Exercise 7.1: Safe Data Processing

Write a function that safely processes a list of nullable strings, filtering out nulls, converting to uppercase, and returning only strings longer than 3 characters.

```kotlin
fun processStrings(input: List<String?>): List<String> {
    return input
        .filterNotNull()
        .map { it.uppercase() }
        .filter { it.length > 3 }
}

fun main() {
    val data = listOf("hello", null, "hi", "world", null, "kot", "kotlin")
    val result = processStrings(data)
    println(result)  // [HELLO, WORLD, KOTLIN]
}
```

## Chapter 8: Classes and Objects

### Basic Class Declaration

```kotlin
class Person {
    var name: String = ""
    var age: Int = 0

    fun introduce() {
        println("My name is $name and I am $age years old")
    }
}

fun main() {
    val person = Person()
    person.name = "Alice"
    person.age = 25
    person.introduce()
}
```

### Primary Constructor

```kotlin
class Person(val name: String, var age: Int) {
    fun introduce() {
        println("My name is $name and I am $age years old")
    }
}

fun main() {
    val person = Person("Alice", 25)
    person.introduce()
}
```

### Init Blocks

```kotlin
class Person(val name: String, var age: Int) {
    init {
        println("Person created: $name")
        require(age >= 0) { "Age cannot be negative" }
    }
}
```

### Secondary Constructors

```kotlin
class Person(val name: String, var age: Int) {
    var email: String = ""

    constructor(name: String, age: Int, email: String) : this(name, age) {
        this.email = email
    }
}
```

### Properties with Custom Getters and Setters

```kotlin
class Rectangle(val width: Int, val height: Int) {
    val area: Int
        get() = width * height

    var name: String = ""
        get() = field.uppercase()
        set(value) {
            field = value.trim()
        }
}
```

### Data Classes

Automatically generates `equals()`, `hashCode()`, `toString()`, and `copy()`:

```kotlin
data class User(val name: String, val age: Int, val email: String)

fun main() {
    val user1 = User("Alice", 25, "alice@example.com")
    val user2 = User("Alice", 25, "alice@example.com")

    println(user1 == user2)  // true (structural equality)
    println(user1)           // User(name=Alice, age=25, email=alice@example.com)

    // Copy with modifications
    val user3 = user1.copy(age = 26)
    println(user3)
}
```

### Exercise 8.1: Bank Account

Create a `BankAccount` class with properties for account number, owner name, and balance. Implement methods for deposit, withdraw, and displaying account information. Use proper validation to prevent negative balances.

```kotlin
class BankAccount(val accountNumber: String, val ownerName: String) {
    private var balance: Double = 0.0

    fun deposit(amount: Double) {
        require(amount > 0) { "Deposit amount must be positive" }
        balance += amount
        println("Deposited: $$amount. New balance: $$balance")
    }

    fun withdraw(amount: Double): Boolean {
        return if (amount > 0 && amount <= balance) {
            balance -= amount
            println("Withdrew: $$amount. New balance: $$balance")
            true
        } else {
            println("Insufficient funds or invalid amount")
            false
        }
    }

    fun displayInfo() {
        println("Account: $accountNumber")
        println("Owner: $ownerName")
        println("Balance: $$balance")
    }
}

fun main() {
    val account = BankAccount("123456", "Alice")
    account.deposit(1000.0)
    account.withdraw(250.0)
    account.withdraw(800.0)
    account.displayInfo()
}
```

## Chapter 9: Inheritance and Interfaces

### Inheritance

All classes in Kotlin inherit from `Any`. To allow inheritance, mark classes with `open`:

```kotlin
open class Animal(val name: String) {
    open fun makeSound() {
        println("Some sound")
    }
}

class Dog(name: String) : Animal(name) {
    override fun makeSound() {
        println("Woof!")
    }
}

class Cat(name: String) : Animal(name) {
    override fun makeSound() {
        println("Meow!")
    }
}

fun main() {
    val dog = Dog("Buddy")
    val cat = Cat("Whiskers")

    dog.makeSound()  // Woof!
    cat.makeSound()  // Meow!
}
```

### Abstract Classes

```kotlin
abstract class Shape {
    abstract val name: String
    abstract fun area(): Double
    abstract fun perimeter(): Double

    fun describe() {
        println("$name - Area: ${area()}, Perimeter: ${perimeter()}")
    }
}

class Circle(val radius: Double) : Shape() {
    override val name = "Circle"
    override fun area() = Math.PI * radius * radius
    override fun perimeter() = 2 * Math.PI * radius
}

class Rectangle(val width: Double, val height: Double) : Shape() {
    override val name = "Rectangle"
    override fun area() = width * height
    override fun perimeter() = 2 * (width + height)
}
```

### Interfaces

```kotlin
interface Drivable {
    val maxSpeed: Int
    fun drive()
    fun stop() {
        println("Vehicle stopped")
    }
}

class Car(override val maxSpeed: Int) : Drivable {
    override fun drive() {
        println("Car driving at max speed: $maxSpeed km/h")
    }
}

class Bicycle(override val maxSpeed: Int) : Drivable {
    override fun drive() {
        println("Bicycle riding at max speed: $maxSpeed km/h")
    }
}
```

### Multiple Interface Implementation

```kotlin
interface Flyable {
    fun fly()
}

interface Swimmable {
    fun swim()
}

class Duck : Flyable, Swimmable {
    override fun fly() {
        println("Duck flying")
    }

    override fun swim() {
        println("Duck swimming")
    }
}
```

### Exercise 9.1: Employee Management System

Create an abstract `Employee` class with properties for name and base salary. Implement concrete classes for different employee types (Manager, Developer, Designer) with different salary calculation methods. Use interfaces to define additional capabilities like `Manageable` or `Trainable`.

```kotlin
interface Manageable {
    fun manageTeam()
}

interface Trainable {
    fun attendTraining(course: String)
}

abstract class Employee(val name: String, val baseSalary: Double) {
    abstract fun calculateSalary(): Double

    fun displayInfo() {
        println("Employee: $name, Salary: $${calculateSalary()}")
    }
}

class Manager(name: String, baseSalary: Double, val teamSize: Int) 
    : Employee(name, baseSalary), Manageable {

    override fun calculateSalary(): Double {
        return baseSalary + (teamSize * 500)
    }

    override fun manageTeam() {
        println("$name manages a team of $teamSize people")
    }
}

class Developer(name: String, baseSalary: Double, val programmingLanguages: Int) 
    : Employee(name, baseSalary), Trainable {

    override fun calculateSalary(): Double {
        return baseSalary + (programmingLanguages * 1000)
    }

    override fun attendTraining(course: String) {
        println("$name is attending training: $course")
    }
}

fun main() {
    val manager = Manager("Alice", 50000.0, 5)
    val developer = Developer("Bob", 60000.0, 3)

    manager.displayInfo()
    manager.manageTeam()

    developer.displayInfo()
    developer.attendTraining("Advanced Kotlin")
}
```

## Chapter 10: Advanced Object-Oriented Features

### Sealed Classes

Restrict class hierarchies to a predefined set of subclasses:

```kotlin
sealed class Result {
    data class Success(val data: String) : Result()
    data class Error(val message: String) : Result()
    object Loading : Result()
}

fun handleResult(result: Result) {
    when (result) {
        is Result.Success -> println("Success: ${result.data}")
        is Result.Error -> println("Error: ${result.message}")
        Result.Loading -> println("Loading...")
    }
}

fun main() {
    handleResult(Result.Success("Data loaded"))
    handleResult(Result.Error("Network error"))
    handleResult(Result.Loading)
}
```

### Sealed Interfaces

```kotlin
sealed interface NetworkResponse

data class Success(val data: String) : NetworkResponse
data class Failure(val error: String) : NetworkResponse
object NetworkError : NetworkResponse

fun processResponse(response: NetworkResponse) {
    when (response) {
        is Success -> println("Received: ${response.data}")
        is Failure -> println("Failed: ${response.error}")
        NetworkError -> println("Network unavailable")
    }
}
```

### Enum Classes

```kotlin
enum class Direction {
    NORTH, SOUTH, EAST, WEST
}

enum class Color(val rgb: Int) {
    RED(0xFF0000),
    GREEN(0x00FF00),
    BLUE(0x0000FF)
}

enum class Status {
    PENDING,
    APPROVED,
    REJECTED;

    fun isComplete(): Boolean = this != PENDING
}

fun main() {
    val direction = Direction.NORTH
    println(direction)

    val color = Color.RED
    println("${color.name}: ${color.rgb}")

    val status = Status.APPROVED
    println("Is complete: ${status.isComplete()}")
}
```

### Object Declarations (Singletons)

```kotlin
object DatabaseConfig {
    const val DATABASE_NAME = "mydb"
    const val VERSION = 1

    fun connect() {
        println("Connecting to $DATABASE_NAME v$VERSION")
    }
}

fun main() {
    DatabaseConfig.connect()
}
```

### Companion Objects

Provide class-level functions and properties:

```kotlin
class User private constructor(val name: String, val age: Int) {
    companion object Factory {
        private var idCounter = 0

        fun create(name: String, age: Int): User {
            idCounter++
            println("Creating user #$idCounter")
            return User(name, age)
        }

        const val MIN_AGE = 18
    }
}

fun main() {
    val user1 = User.create("Alice", 25)
    val user2 = User.create("Bob", 30)
    println("Minimum age: ${User.MIN_AGE}")
}
```

### Nested and Inner Classes

```kotlin
class Outer {
    private val outerProperty = "Outer"

    // Nested class (does not have access to outer class members)
    class Nested {
        fun display() {
            println("Nested class")
        }
    }

    // Inner class (has access to outer class members)
    inner class Inner {
        fun display() {
            println("Inner class accessing: $outerProperty")
        }
    }
}

fun main() {
    val nested = Outer.Nested()
    nested.display()

    val inner = Outer().Inner()
    inner.display()
}
```

### Exercise 10.1: State Machine

Implement a simple state machine for a traffic light using sealed classes. Create states (Red, Yellow, Green) and implement a function to transition to the next state.

```kotlin
sealed class TrafficLight {
    abstract fun next(): TrafficLight
    abstract val duration: Int

    object Red : TrafficLight() {
        override fun next() = Green
        override val duration = 30
    }

    object Yellow : TrafficLight() {
        override fun next() = Red
        override val duration = 3
    }

    object Green : TrafficLight() {
        override fun next() = Yellow
        override val duration = 25
    }
}

fun main() {
    var current: TrafficLight = TrafficLight.Red

    repeat(5) {
        val state = when (current) {
            TrafficLight.Red -> "RED"
            TrafficLight.Yellow -> "YELLOW"
            TrafficLight.Green -> "GREEN"
        }
        println("Current: $state (${current.duration}s)")
        current = current.next()
    }
}
```

## Chapter 11: Extension Functions and Properties

### Extension Functions

Add functionality to existing classes without modifying their source code:

```kotlin
fun String.isPalindrome(): Boolean {
    val cleaned = this.lowercase().filter { it.isLetterOrDigit() }
    return cleaned == cleaned.reversed()
}

fun Int.isEven(): Boolean = this % 2 == 0

fun List<Int>.secondLargest(): Int? {
    val sorted = this.distinct().sortedDescending()
    return if (sorted.size >= 2) sorted[1] else null
}

fun main() {
    println("racecar".isPalindrome())  // true
    println("hello".isPalindrome())    // false

    println(4.isEven())   // true
    println(7.isEven())   // false

    val numbers = listOf(5, 2, 8, 2, 9, 1)
    println(numbers.secondLargest())  // 8
}
```

### Extension Properties

```kotlin
val String.lastChar: Char
    get() = this[length - 1]

val List<Int>.sumOfSquares: Int
    get() = this.sumOf { it * it }

fun main() {
    println("Kotlin".lastChar)  // n

    val numbers = listOf(1, 2, 3, 4)
    println(numbers.sumOfSquares)  // 30
}
```

### Extensions are Resolved Statically

```kotlin
open class Shape
class Rectangle : Shape()

fun Shape.getName() = "Shape"
fun Rectangle.getName() = "Rectangle"

fun printName(shape: Shape) {
    println(shape.getName())
}

fun main() {
    printName(Rectangle())  // Prints "Shape" (static resolution)
}
```

### Exercise 11.1: String Utilities

Create extension functions for String to: count vowels, remove digits, and capitalize each word. Create an extension property that returns the word count.

```kotlin
fun String.countVowels(): Int {
    return this.lowercase().count { it in "aeiou" }
}

fun String.removeDigits(): String {
    return this.filter { !it.isDigit() }
}

fun String.capitalizeWords(): String {
    return this.split(" ").joinToString(" ") { 
        it.replaceFirstChar { c -> c.uppercase() } 
    }
}

val String.wordCount: Int
    get() = this.trim().split("\s+".toRegex()).size

fun main() {
    val text = "Hello World 123"

    println(text.countVowels())        // 3
    println(text.removeDigits())       // Hello World 
    println(text.capitalizeWords())    // Hello World 123
    println(text.wordCount)            // 3
}
```

## Chapter 12: Generics

### Generic Functions

```kotlin
fun <T> printItem(item: T) {
    println(item)
}

fun <T> List<T>.secondOrNull(): T? {
    return if (this.size >= 2) this[1] else null
}

fun main() {
    printItem(42)
    printItem("Hello")
    printItem(3.14)

    println(listOf(1, 2, 3).secondOrNull())      // 2
    println(listOf("a").secondOrNull())          // null
}
```

### Generic Classes

```kotlin
class Box<T>(var content: T) {
    fun getContent(): T = content
}

fun main() {
    val intBox = Box(42)
    val stringBox = Box("Hello")

    println(intBox.getContent())     // 42
    println(stringBox.getContent())  // Hello
}
```

### Type Constraints

```kotlin
fun <T : Comparable<T>> maxOf(a: T, b: T): T {
    return if (a > b) a else b
}

fun <T : Number> sum(a: T, b: T): Double {
    return a.toDouble() + b.toDouble()
}

fun main() {
    println(maxOf(5, 10))         // 10
    println(maxOf("apple", "banana"))  // banana
    println(sum(5, 10))           // 15.0
    println(sum(3.5, 2.7))        // 6.2
}
```

### Variance: In and Out

```kotlin
// Covariance (out)
class Producer<out T>(val value: T) {
    fun produce(): T = value
}

// Contravariance (in)
class Consumer<in T> {
    fun consume(item: T) {
        println("Consuming: $item")
    }
}

fun main() {
    val stringProducer: Producer<String> = Producer("Hello")
    val anyProducer: Producer<Any> = stringProducer  // Valid (covariance)

    val anyConsumer: Consumer<Any> = Consumer()
    val stringConsumer: Consumer<String> = anyConsumer  // Valid (contravariance)
    stringConsumer.consume("Kotlin")
}
```

### Reified Type Parameters

Access type information at runtime with inline functions:

```kotlin
inline fun <reified T> isInstance(value: Any): Boolean {
    return value is T
}

inline fun <reified T> List<*>.filterIsInstance(): List<T> {
    return this.filter { it is T }.map { it as T }
}

fun main() {
    println(isInstance<String>("Hello"))  // true
    println(isInstance<Int>("Hello"))     // false

    val mixed = listOf(1, "two", 3, "four", 5)
    val strings = mixed.filterIsInstance<String>()
    println(strings)  // [two, four]
}
```

### Exercise 12.1: Generic Stack

Implement a generic Stack class with push, pop, peek, and isEmpty operations. Test with different types.

```kotlin
class Stack<T> {
    private val items = mutableListOf<T>()

    fun push(item: T) {
        items.add(item)
    }

    fun pop(): T? {
        return if (items.isNotEmpty()) items.removeAt(items.size - 1) else null
    }

    fun peek(): T? {
        return items.lastOrNull()
    }

    fun isEmpty(): Boolean = items.isEmpty()

    fun size(): Int = items.size

    override fun toString(): String = items.toString()
}

fun main() {
    val intStack = Stack<Int>()
    intStack.push(1)
    intStack.push(2)
    intStack.push(3)
    println("Stack: $intStack")
    println("Pop: ${intStack.pop()}")
    println("Peek: ${intStack.peek()}")
    println("Size: ${intStack.size()}")

    val stringStack = Stack<String>()
    stringStack.push("Kotlin")
    stringStack.push("Java")
    println("String stack: $stringStack")
}
```

## Chapter 13: Delegated Properties

### Standard Delegates: Lazy

Lazy initialization delays computation until first access:

```kotlin
class DataLoader {
    val expensiveData: String by lazy {
        println("Loading expensive data...")
        Thread.sleep(1000)
        "Important Data"
    }
}

fun main() {
    val loader = DataLoader()
    println("Loader created")
    println(loader.expensiveData)  // Loads here
    println(loader.expensiveData)  // Uses cached value
}
```

### Observable and Vetoable

```kotlin
import kotlin.properties.Delegates

class User {
    var name: String by Delegates.observable("Initial") { prop, old, new ->
        println("${prop.name}: $old -> $new")
    }

    var age: Int by Delegates.vetoable(0) { prop, old, new ->
        new >= 0  // Only allow non-negative ages
    }
}

fun main() {
    val user = User()
    user.name = "Alice"  // name: Initial -> Alice
    user.name = "Bob"    // name: Alice -> Bob

    user.age = 25
    println(user.age)    // 25
    user.age = -5        // Rejected
    println(user.age)    // Still 25
}
```

### Storing Properties in a Map

```kotlin
class DynamicUser(map: Map<String, Any?>) {
    val name: String by map
    val age: Int by map
    val email: String by map
}

fun main() {
    val user = DynamicUser(mapOf(
        "name" to "Alice",
        "age" to 25,
        "email" to "alice@example.com"
    ))

    println("${user.name}, ${user.age}, ${user.email}")
}
```

### Custom Delegates

```kotlin
import kotlin.reflect.KProperty

class LoggingDelegate<T>(private var value: T) {
    operator fun getValue(thisRef: Any?, property: KProperty<*>): T {
        println("Getting ${property.name}: $value")
        return value
    }

    operator fun setValue(thisRef: Any?, property: KProperty<*>, newValue: T) {
        println("Setting ${property.name}: $value -> $newValue")
        value = newValue
    }
}

class Configuration {
    var timeout: Int by LoggingDelegate(30)
}

fun main() {
    val config = Configuration()
    println(config.timeout)
    config.timeout = 60
    println(config.timeout)
}
```

### Exercise 13.1: Validation Delegate

Create a custom property delegate that validates string length. Use it for username and password fields with different minimum lengths.

```kotlin
import kotlin.reflect.KProperty

class MinLengthDelegate(private val minLength: Int) {
    private var value: String = ""

    operator fun getValue(thisRef: Any?, property: KProperty<*>): String {
        return value
    }

    operator fun setValue(thisRef: Any?, property: KProperty<*>, newValue: String) {
        if (newValue.length >= minLength) {
            value = newValue
            println("${property.name} set to: $newValue")
        } else {
            println("${property.name} must be at least $minLength characters")
        }
    }
}

class UserAccount {
    var username: String by MinLengthDelegate(3)
    var password: String by MinLengthDelegate(8)
}

fun main() {
    val account = UserAccount()
    account.username = "ab"       // Too short
    account.username = "alice"    // Valid
    account.password = "12345"    // Too short
    account.password = "securepass123"  // Valid
}
```

## Chapter 14: Scope Functions

Kotlin provides five scope functions: `let`, `run`, `with`, `apply`, and `also`. They execute a block of code in the context of an object.

### Let

Execute code with non-null values:

```kotlin
val name: String? = "Alice"
name?.let {
    println("Name length: ${it.length}")
    println("Uppercase: ${it.uppercase()}")
}

// Transform and return
val length = name?.let { it.length } ?: 0
```

### Run

Execute code and return result:

```kotlin
val result = "Hello".run {
    println("Original: $this")
    println("Length: $length")
    uppercase()
}
println(result)  // HELLO
```

### With

Group function calls on an object:

```kotlin
val numbers = mutableListOf(1, 2, 3)
with(numbers) {
    add(4)
    add(5)
    println("Size: $size")
    println(this)
}
```

### Apply

Configure objects (returns the object itself):

```kotlin
data class Person(var name: String = "", var age: Int = 0)

val person = Person().apply {
    name = "Alice"
    age = 25
}
println(person)
```

### Also

Perform additional operations (returns the object):

```kotlin
val numbers = mutableListOf(1, 2, 3)
    .also { println("Initial list: $it") }
    .also { it.add(4) }
    .also { println("After adding: $it") }
```

### Choosing the Right Scope Function

Use `let` for null safety and transformations. Use `run` when you need both object context and return value. Use `with` for calling multiple functions on an object without needing the result. Use `apply` for object configuration. Use `also` for additional side effects while keeping the chain.

### Exercise 14.1: Builder Pattern with Scope Functions

Create a `StringBuilder` wrapper using scope functions to build formatted text.

```kotlin
fun buildReport(name: String, items: List<String>): String {
    return StringBuilder().apply {
        append("Report for: $name
")
        append("=" * 30)
        append("
")
    }.also {
        items.forEachIndexed { index, item ->
            it.append("${index + 1}. $item
")
        }
    }.run {
        append("=" * 30)
        append("
Total items: ${items.size}")
        toString()
    }
}

fun main() {
    val report = buildReport("Alice", listOf("Item A", "Item B", "Item C"))
    println(report)
}
```

## Chapter 15: Coroutines

Coroutines provide lightweight concurrency for asynchronous programming without blocking threads.

### Setup

Add dependencies to `build.gradle.kts`:

```kotlin
dependencies {
    implementation("org.jetbrains.kotlinx:kotlinx-coroutines-core:1.7.3")
}
```

### Basic Coroutine

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    launch {
        delay(1000L)
        println("World!")
    }
    println("Hello,")
}
```

### Suspending Functions

Functions marked with `suspend` can be paused and resumed:

```kotlin
suspend fun fetchData(): String {
    delay(1000L)  // Simulates network call
    return "Data from server"
}

fun main() = runBlocking {
    println("Fetching...")
    val data = fetchData()
    println(data)
}
```

### Async and Await

Run coroutines concurrently and wait for results:

```kotlin
import kotlinx.coroutines.*

suspend fun fetchUser(): String {
    delay(1000L)
    return "User data"
}

suspend fun fetchPosts(): String {
    delay(1500L)
    return "Posts data"
}

fun main() = runBlocking {
    val user = async { fetchUser() }
    val posts = async { fetchPosts() }

    println("Fetching data...")
    println(user.await())
    println(posts.await())
}
```

### Coroutine Contexts and Dispatchers

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    // Default dispatcher (optimized for CPU-intensive work)
    launch(Dispatchers.Default) {
        println("Default: ${Thread.currentThread().name}")
    }

    // IO dispatcher (optimized for IO operations)
    launch(Dispatchers.IO) {
        println("IO: ${Thread.currentThread().name}")
    }

    // Unconfined dispatcher
    launch(Dispatchers.Unconfined) {
        println("Unconfined: ${Thread.currentThread().name}")
    }
}
```

### Structured Concurrency

```kotlin
import kotlinx.coroutines.*

suspend fun performTask(taskId: Int): String {
    delay(1000L)
    return "Task $taskId completed"
}

fun main() = runBlocking {
    coroutineScope {
        val jobs = List(5) { taskId ->
            async {
                performTask(taskId)
            }
        }
        jobs.forEach { println(it.await()) }
    }
    println("All tasks completed")
}
```

### Exception Handling

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    val job = launch {
        try {
            repeat(1000) { i ->
                println("Job: $i")
                delay(500L)
            }
        } catch (e: CancellationException) {
            println("Job cancelled")
        }
    }

    delay(1300L)
    println("Cancelling job")
    job.cancelAndJoin()
    println("Done")
}
```

### Exercise 15.1: Concurrent Data Processing

Create a program that fetches data from multiple sources concurrently, processes the results, and combines them.

```kotlin
import kotlinx.coroutines.*

data class ApiResponse(val source: String, val data: String)

suspend fun fetchFromApi(apiName: String, delayMs: Long): ApiResponse {
    println("Fetching from $apiName...")
    delay(delayMs)
    return ApiResponse(apiName, "Data from $apiName")
}

suspend fun processData(response: ApiResponse): String {
    delay(500L)
    return "${response.source}: ${response.data.uppercase()}"
}

fun main() = runBlocking {
    val startTime = System.currentTimeMillis()

    val results = coroutineScope {
        val api1 = async { fetchFromApi("API-1", 1000L) }
        val api2 = async { fetchFromApi("API-2", 1500L) }
        val api3 = async { fetchFromApi("API-3", 800L) }

        listOf(api1, api2, api3).map { it.await() }
    }

    val processed = results.map { processData(it) }
    processed.forEach { println(it) }

    val duration = System.currentTimeMillis() - startTime
    println("Total time: ${duration}ms")
}
```

## Chapter 16: Exception Handling

### Try-Catch-Finally

```kotlin
fun divide(a: Int, b: Int): Int {
    return try {
        a / b
    } catch (e: ArithmeticException) {
        println("Cannot divide by zero")
        0
    } finally {
        println("Division operation completed")
    }
}

fun main() {
    println(divide(10, 2))
    println(divide(10, 0))
}
```

### Try as an Expression

```kotlin
val result: Int = try {
    "123".toInt()
} catch (e: NumberFormatException) {
    0
}
```

### Multiple Catch Blocks

```kotlin
fun processInput(input: String) {
    try {
        val number = input.toInt()
        val result = 100 / number
        println("Result: $result")
    } catch (e: NumberFormatException) {
        println("Invalid number format")
    } catch (e: ArithmeticException) {
        println("Cannot divide by zero")
    } catch (e: Exception) {
        println("Unknown error: ${e.message}")
    }
}
```

### Custom Exceptions

```kotlin
class InvalidAgeException(message: String) : Exception(message)

fun setAge(age: Int) {
    if (age < 0 || age > 150) {
        throw InvalidAgeException("Age must be between 0 and 150")
    }
    println("Age set to: $age")
}

fun main() {
    try {
        setAge(25)
        setAge(200)
    } catch (e: InvalidAgeException) {
        println("Error: ${e.message}")
    }
}
```

### Exercise 16.1: Safe File Reader

Write a function that safely reads a number from user input, handles various exceptions, and returns a default value if parsing fails.

```kotlin
fun readNumberSafely(input: String, default: Int = 0): Int {
    return try {
        val number = input.trim().toInt()
        require(number >= 0) { "Number must be non-negative" }
        number
    } catch (e: NumberFormatException) {
        println("Invalid number format, using default: $default")
        default
    } catch (e: IllegalArgumentException) {
        println("${e.message}, using default: $default")
        default
    }
}

fun main() {
    println(readNumberSafely("42"))        // 42
    println(readNumberSafely("abc"))       // 0
    println(readNumberSafely("-5"))        // 0
    println(readNumberSafely("  100  "))   // 100
}
```

## Chapter 17: Type-Safe Builders and DSLs

Type-safe builders enable creating domain-specific languages with Kotlin's lambda with receiver feature.

### Lambda with Receiver

```kotlin
fun buildString(action: StringBuilder.() -> Unit): String {
    val builder = StringBuilder()
    builder.action()
    return builder.toString()
}

fun main() {
    val result = buildString {
        append("Hello")
        append(" ")
        append("World")
    }
    println(result)  // Hello World
}
```

### HTML Builder Example

```kotlin
@DslMarker
annotation class HtmlDsl

@HtmlDsl
class HTML {
    private val content = StringBuilder()

    fun head(init: Head.() -> Unit) {
        val head = Head()
        head.init()
        content.append("<head>${head.build()}</head>")
    }

    fun body(init: Body.() -> Unit) {
        val body = Body()
        body.init()
        content.append("<body>${body.build()}</body>")
    }

    fun build(): String = "<html>$content</html>"
}

@HtmlDsl
class Head {
    private val content = StringBuilder()

    fun title(text: String) {
        content.append("<title>$text</title>")
    }

    fun build(): String = content.toString()
}

@HtmlDsl
class Body {
    private val content = StringBuilder()

    fun h1(text: String) {
        content.append("<h1>$text</h1>")
    }

    fun p(text: String) {
        content.append("<p>$text</p>")
    }

    fun build(): String = content.toString()
}

fun html(init: HTML.() -> Unit): String {
    val html = HTML()
    html.init()
    return html.build()
}

fun main() {
    val page = html {
        head {
            title("My Page")
        }
        body {
            h1("Welcome")
            p("This is a paragraph")
        }
    }
    println(page)
}
```

### Configuration DSL

```kotlin
@DslMarker
annotation class ConfigDsl

@ConfigDsl
class DatabaseConfig {
    var host: String = "localhost"
    var port: Int = 5432
    var username: String = ""
    var password: String = ""

    fun connection(init: ConnectionPool.() -> Unit) {
        val pool = ConnectionPool()
        pool.init()
        println("Connection pool: max=${pool.maxConnections}, min=${pool.minConnections}")
    }
}

@ConfigDsl
class ConnectionPool {
    var maxConnections: Int = 10
    var minConnections: Int = 2
}

fun database(init: DatabaseConfig.() -> Unit): DatabaseConfig {
    val config = DatabaseConfig()
    config.init()
    return config
}

fun main() {
    val config = database {
        host = "db.example.com"
        port = 3306
        username = "admin"
        password = "secret"

        connection {
            maxConnections = 50
            minConnections = 5
        }
    }

    println("Database: ${config.host}:${config.port}")
}
```

### Exercise 17.1: REST API DSL

Create a simple DSL for building REST API route definitions with methods (GET, POST), paths, and handlers.

```kotlin
@DslMarker
annotation class ApiDsl

@ApiDsl
class ApiBuilder {
    private val routes = mutableListOf<Route>()

    fun get(path: String, handler: () -> String) {
        routes.add(Route("GET", path, handler))
    }

    fun post(path: String, handler: () -> String) {
        routes.add(Route("POST", path, handler))
    }

    fun getRoutes(): List<Route> = routes
}

data class Route(val method: String, val path: String, val handler: () -> String)

fun api(init: ApiBuilder.() -> Unit): List<Route> {
    val builder = ApiBuilder()
    builder.init()
    return builder.getRoutes()
}

fun main() {
    val routes = api {
        get("/users") {
            "List of users"
        }

        get("/users/123") {
            "User 123 details"
        }

        post("/users") {
            "Create new user"
        }
    }

    routes.forEach {
        println("${it.method} ${it.path} -> ${it.handler()}")
    }
}
```

## Chapter 18: Kotlin and Java Interoperability

### Calling Java from Kotlin

Kotlin provides seamless Java interoperability:

```kotlin
// Java ArrayList
val list = java.util.ArrayList<String>()
list.add("Kotlin")
list.add("Java")

// Java Date
val date = java.util.Date()
println(date)

// Java static methods
val sqrt = Math.sqrt(16.0)
println(sqrt)
```

### Handling Java Nullability

```kotlin
// Platform types from Java (Type!)
val javaString: String = getJavaString()  // May throw NPE
val kotlinString: String? = getJavaString()  // Safe

// Using @Nullable and @NotNull annotations in Java helps Kotlin
```

### Calling Kotlin from Java

Kotlin generates Java-compatible bytecode. Top-level functions become static methods:

```kotlin
// Kotlin file: Utils.kt
package com.example

fun greet(name: String) {
    println("Hello, $name")
}

// Called from Java:
// UtilsKt.greet("Alice");
```

### JvmStatic and JvmField

```kotlin
class MyClass {
    companion object {
        @JvmStatic
        fun staticMethod() {
            println("Can be called as MyClass.staticMethod() from Java")
        }

        @JvmField
        val CONSTANT = "Accessible as MyClass.CONSTANT from Java"
    }
}
```

### JvmOverloads

Generate overloaded methods for functions with default parameters:

```kotlin
@JvmOverloads
fun greet(name: String, greeting: String = "Hello") {
    println("$greeting, $name")
}

// Java can call:
// greet("Alice")
// greet("Alice", "Hi")
```

### Exercise 18.1: Wrapper for Java Library

Create Kotlin extension functions for Java's `LocalDate` to add convenient date operations.

```kotlin
import java.time.LocalDate
import java.time.temporal.ChronoUnit

fun LocalDate.addDays(days: Long): LocalDate = this.plusDays(days)
fun LocalDate.addWeeks(weeks: Long): LocalDate = this.plusWeeks(weeks)
fun LocalDate.daysBetween(other: LocalDate): Long = ChronoUnit.DAYS.between(this, other)
fun LocalDate.isWeekend(): Boolean = this.dayOfWeek.value in 6..7

fun main() {
    val today = LocalDate.now()
    val nextWeek = today.addWeeks(1)
    val tomorrow = today.addDays(1)

    println("Today: $today")
    println("Tomorrow: $tomorrow")
    println("Next week: $nextWeek")
    println("Days between: ${today.daysBetween(nextWeek)}")
    println("Is weekend: ${today.isWeekend()}")
}
```

## Chapter 19: Gradle with Kotlin DSL

### Basic Build Script Structure

```kotlin
// build.gradle.kts
plugins {
    kotlin("jvm") version "1.9.20"
    application
}

group = "com.example"
version = "1.0-SNAPSHOT"

repositories {
    mavenCentral()
}

dependencies {
    implementation(kotlin("stdlib"))
    implementation("org.jetbrains.kotlinx:kotlinx-coroutines-core:1.7.3")
    testImplementation(kotlin("test"))
}

tasks.test {
    useJUnitPlatform()
}

kotlin {
    jvmToolchain(17)
}

application {
    mainClass.set("com.example.MainKt")
}
```

### Multi-Module Project

```kotlin
// settings.gradle.kts
rootProject.name = "my-project"
include("core", "web", "android")

// Root build.gradle.kts
plugins {
    kotlin("jvm") version "1.9.20" apply false
}

allprojects {
    repositories {
        mavenCentral()
    }
}

// Module build.gradle.kts
plugins {
    kotlin("jvm")
}

dependencies {
    implementation(project(":core"))
}
```

### Custom Tasks

```kotlin
tasks.register("hello") {
    doLast {
        println("Hello from custom task")
    }
}

tasks.register<Copy>("copyDocs") {
    from("src/docs")
    into("build/docs")
}
```

## Chapter 20: Ktor for Backend Development

### Setup

```kotlin
// build.gradle.kts
plugins {
    kotlin("jvm") version "1.9.20"
    id("io.ktor.plugin") version "2.3.6"
}

dependencies {
    implementation("io.ktor:ktor-server-core:2.3.6")
    implementation("io.ktor:ktor-server-netty:2.3.6")
    implementation("io.ktor:ktor-server-content-negotiation:2.3.6")
    implementation("io.ktor:ktor-serialization-kotlinx-json:2.3.6")
}
```

### Basic Server

```kotlin
import io.ktor.server.application.*
import io.ktor.server.engine.*
import io.ktor.server.netty.*
import io.ktor.server.response.*
import io.ktor.server.routing.*

fun main() {
    embeddedServer(Netty, port = 8080) {
        routing {
            get("/") {
                call.respondText("Hello, Ktor!")
            }

            get("/users/{id}") {
                val id = call.parameters["id"]
                call.respondText("User ID: $id")
            }

            post("/users") {
                call.respondText("User created")
            }
        }
    }.start(wait = true)
}
```

### JSON API with Serialization

```kotlin
import io.ktor.serialization.kotlinx.json.*
import io.ktor.server.application.*
import io.ktor.server.plugins.contentnegotiation.*
import io.ktor.server.request.*
import io.ktor.server.response.*
import io.ktor.server.routing.*
import kotlinx.serialization.Serializable

@Serializable
data class User(val id: Int, val name: String, val email: String)

fun Application.module() {
    install(ContentNegotiation) {
        json()
    }

    val users = mutableListOf(
        User(1, "Alice", "alice@example.com"),
        User(2, "Bob", "bob@example.com")
    )

    routing {
        get("/api/users") {
            call.respond(users)
        }

        get("/api/users/{id}") {
            val id = call.parameters["id"]?.toIntOrNull()
            val user = users.find { it.id == id }
            if (user != null) {
                call.respond(user)
            } else {
                call.respondText("User not found", status = io.ktor.http.HttpStatusCode.NotFound)
            }
        }

        post("/api/users") {
            val user = call.receive<User>()
            users.add(user)
            call.respond(io.ktor.http.HttpStatusCode.Created, user)
        }
    }
}
```

### Exercise 20.1: Simple REST API

Create a REST API for a todo list with endpoints to list, create, update, and delete tasks.

```kotlin
import io.ktor.serialization.kotlinx.json.*
import io.ktor.server.application.*
import io.ktor.server.engine.*
import io.ktor.server.netty.*
import io.ktor.server.plugins.contentnegotiation.*
import io.ktor.server.request.*
import io.ktor.server.response.*
import io.ktor.server.routing.*
import kotlinx.serialization.Serializable

@Serializable
data class Task(val id: Int, var title: String, var completed: Boolean = false)

fun main() {
    embeddedServer(Netty, port = 8080) {
        install(ContentNegotiation) {
            json()
        }

        val tasks = mutableListOf(
            Task(1, "Learn Kotlin", false),
            Task(2, "Build REST API", false)
        )
        var nextId = 3

        routing {
            get("/tasks") {
                call.respond(tasks)
            }

            get("/tasks/{id}") {
                val id = call.parameters["id"]?.toIntOrNull()
                val task = tasks.find { it.id == id }
                if (task != null) {
                    call.respond(task)
                } else {
                    call.respondText("Task not found", status = io.ktor.http.HttpStatusCode.NotFound)
                }
            }

            post("/tasks") {
                val task = call.receive<Task>().copy(id = nextId++)
                tasks.add(task)
                call.respond(io.ktor.http.HttpStatusCode.Created, task)
            }

            put("/tasks/{id}") {
                val id = call.parameters["id"]?.toIntOrNull()
                val index = tasks.indexOfFirst { it.id == id }
                if (index != -1) {
                    val updatedTask = call.receive<Task>()
                    tasks[index] = updatedTask.copy(id = id!!)
                    call.respond(tasks[index])
                } else {
                    call.respondText("Task not found", status = io.ktor.http.HttpStatusCode.NotFound)
                }
            }

            delete("/tasks/{id}") {
                val id = call.parameters["id"]?.toIntOrNull()
                val removed = tasks.removeIf { it.id == id }
                if (removed) {
                    call.respondText("Task deleted")
                } else {
                    call.respondText("Task not found", status = io.ktor.http.HttpStatusCode.NotFound)
                }
            }
        }
    }.start(wait = true)
}
```

## Chapter 21: Database Access

### Room (Android)

Setup in `build.gradle.kts`:

```kotlin
plugins {
    id("com.google.devtools.ksp") version "1.9.20-1.0.14"
}

dependencies {
    implementation("androidx.room:room-runtime:2.6.0")
    implementation("androidx.room:room-ktx:2.6.0")
    ksp("androidx.room:room-compiler:2.6.0")
}
```

Define entities, DAOs, and database:

```kotlin
import androidx.room.*

@Entity(tableName = "users")
data class User(
    @PrimaryKey(autoGenerate = true) val id: Int = 0,
    @ColumnInfo(name = "name") val name: String,
    @ColumnInfo(name = "email") val email: String
)

@Dao
interface UserDao {
    @Query("SELECT * FROM users")
    suspend fun getAllUsers(): List<User>

    @Query("SELECT * FROM users WHERE id = :userId")
    suspend fun getUserById(userId: Int): User?

    @Insert
    suspend fun insertUser(user: User)

    @Update
    suspend fun updateUser(user: User)

    @Delete
    suspend fun deleteUser(user: User)
}

@Database(entities = [User::class], version = 1)
abstract class AppDatabase : RoomDatabase() {
    abstract fun userDao(): UserDao
}

// Usage
val db = Room.databaseBuilder(
    context,
    AppDatabase::class.java,
    "app-database"
).build()

val userDao = db.userDao()
```

### Exposed (JVM)

```kotlin
// build.gradle.kts
dependencies {
    implementation("org.jetbrains.exposed:exposed-core:0.44.1")
    implementation("org.jetbrains.exposed:exposed-dao:0.44.1")
    implementation("org.jetbrains.exposed:exposed-jdbc:0.44.1")
    implementation("com.h2database:h2:2.2.224")
}
```

```kotlin
import org.jetbrains.exposed.sql.*
import org.jetbrains.exposed.sql.transactions.transaction

object Users : Table() {
    val id = integer("id").autoIncrement()
    val name = varchar("name", 50)
    val email = varchar("email", 100)
    override val primaryKey = PrimaryKey(id)
}

fun main() {
    Database.connect("jdbc:h2:mem:test", driver = "org.h2.Driver")

    transaction {
        addLogger(StdOutSqlLogger)

        SchemaUtils.create(Users)

        Users.insert {
            it[name] = "Alice"
            it[email] = "alice@example.com"
        }

        Users.insert {
            it[name] = "Bob"
            it[email] = "bob@example.com"
        }

        println("All users:")
        Users.selectAll().forEach {
            println("${it[Users.id]}: ${it[Users.name]} - ${it[Users.email]}")
        }
    }
}
```

### Exercise 21.1: Product Inventory

Using Exposed, create a product inventory system with tables for products and categories. Implement functions to add products, update stock, and query by category.

```kotlin
import org.jetbrains.exposed.sql.*
import org.jetbrains.exposed.sql.transactions.transaction

object Categories : Table() {
    val id = integer("id").autoIncrement()
    val name = varchar("name", 50)
    override val primaryKey = PrimaryKey(id)
}

object Products : Table() {
    val id = integer("id").autoIncrement()
    val name = varchar("name", 100)
    val price = decimal("price", 10, 2)
    val stock = integer("stock")
    val categoryId = integer("category_id").references(Categories.id)
    override val primaryKey = PrimaryKey(id)
}

fun addProduct(name: String, price: Double, stock: Int, categoryId: Int) {
    transaction {
        Products.insert {
            it[Products.name] = name
            it[Products.price] = price.toBigDecimal()
            it[Products.stock] = stock
            it[Products.categoryId] = categoryId
        }
    }
}

fun updateStock(productId: Int, newStock: Int) {
    transaction {
        Products.update({ Products.id eq productId }) {
            it[stock] = newStock
        }
    }
}

fun getProductsByCategory(categoryId: Int): List<ResultRow> {
    return transaction {
        Products.select { Products.categoryId eq categoryId }.toList()
    }
}

fun main() {
    Database.connect("jdbc:h2:mem:test", driver = "org.h2.Driver")

    transaction {
        addLogger(StdOutSqlLogger)
        SchemaUtils.create(Categories, Products)

        val electronicsId = Categories.insert {
            it[name] = "Electronics"
        } get Categories.id

        addProduct("Laptop", 999.99, 10, electronicsId)
        addProduct("Mouse", 29.99, 50, electronicsId)

        updateStock(1, 8)

        println("Electronics products:")
        getProductsByCategory(electronicsId).forEach {
            println("${it[Products.name]}: $${it[Products.price]} (${it[Products.stock]} in stock)")
        }
    }
}
```

## Chapter 22: Android Development with Kotlin

### ViewModel and LiveData

```kotlin
import androidx.lifecycle.ViewModel
import androidx.lifecycle.LiveData
import androidx.lifecycle.MutableLiveData

data class User(val name: String, val age: Int)

class UserViewModel : ViewModel() {
    private val _user = MutableLiveData<User>()
    val user: LiveData<User> = _user

    private val _isLoading = MutableLiveData<Boolean>()
    val isLoading: LiveData<Boolean> = _isLoading

    fun loadUser() {
        _isLoading.value = true
        // Simulate network call
        _user.value = User("Alice", 25)
        _isLoading.value = false
    }

    fun updateUserName(newName: String) {
        _user.value = _user.value?.copy(name = newName)
    }
}
```

### Observing in Activity

```kotlin
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import androidx.lifecycle.ViewModelProvider

class MainActivity : AppCompatActivity() {
    private lateinit var viewModel: UserViewModel

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        viewModel = ViewModelProvider(this).get(UserViewModel::class.java)

        viewModel.user.observe(this) { user ->
            // Update UI with user data
            println("User: ${user.name}, ${user.age}")
        }

        viewModel.isLoading.observe(this) { isLoading ->
            // Show/hide loading indicator
            println("Loading: $isLoading")
        }

        viewModel.loadUser()
    }
}
```

### StateFlow (Modern Alternative)

```kotlin
import androidx.lifecycle.ViewModel
import kotlinx.coroutines.flow.MutableStateFlow
import kotlinx.coroutines.flow.StateFlow
import kotlinx.coroutines.flow.asStateFlow

class ModernViewModel : ViewModel() {
    private val _uiState = MutableStateFlow(UiState())
    val uiState: StateFlow<UiState> = _uiState.asStateFlow()

    fun updateName(name: String) {
        _uiState.value = _uiState.value.copy(name = name)
    }
}

data class UiState(
    val name: String = "",
    val isLoading: Boolean = false
)
```

### Jetpack Compose Basic Example

```kotlin
import androidx.compose.foundation.layout.*
import androidx.compose.material3.*
import androidx.compose.runtime.*
import androidx.compose.ui.Modifier
import androidx.compose.ui.unit.dp

@Composable
fun UserScreen(viewModel: UserViewModel) {
    val user by viewModel.user.observeAsState()

    Column(modifier = Modifier.padding(16.dp)) {
        Text(text = "Name: ${user?.name ?: "Loading..."}")
        Text(text = "Age: ${user?.age ?: 0}")

        Spacer(modifier = Modifier.height(16.dp))

        Button(onClick = { viewModel.loadUser() }) {
            Text("Refresh")
        }
    }
}
```

### Exercise 22.1: Counter App Architecture

Create a simple counter app using ViewModel with increment, decrement, and reset operations. Use StateFlow for state management.

```kotlin
import androidx.lifecycle.ViewModel
import kotlinx.coroutines.flow.MutableStateFlow
import kotlinx.coroutines.flow.StateFlow
import kotlinx.coroutines.flow.asStateFlow
import kotlinx.coroutines.flow.update

data class CounterState(
    val count: Int = 0,
    val history: List<Int> = emptyList()
)

class CounterViewModel : ViewModel() {
    private val _state = MutableStateFlow(CounterState())
    val state: StateFlow<CounterState> = _state.asStateFlow()

    fun increment() {
        _state.update { currentState ->
            val newCount = currentState.count + 1
            currentState.copy(
                count = newCount,
                history = currentState.history + newCount
            )
        }
    }

    fun decrement() {
        _state.update { currentState ->
            val newCount = currentState.count - 1
            currentState.copy(
                count = newCount,
                history = currentState.history + newCount
            )
        }
    }

    fun reset() {
        _state.update {
            CounterState()
        }
    }
}

// Usage in Compose
@Composable
fun CounterScreen(viewModel: CounterViewModel) {
    val state by viewModel.state.collectAsState()

    Column(modifier = Modifier.padding(16.dp)) {
        Text("Count: ${state.count}", style = MaterialTheme.typography.headlineLarge)

        Row {
            Button(onClick = { viewModel.increment() }) {
                Text("Increment")
            }
            Spacer(modifier = Modifier.width(8.dp))
            Button(onClick = { viewModel.decrement() }) {
                Text("Decrement")
            }
            Spacer(modifier = Modifier.width(8.dp))
            Button(onClick = { viewModel.reset() }) {
                Text("Reset")
            }
        }

        Spacer(modifier = Modifier.height(16.dp))
        Text("History: ${state.history.joinToString(", ")}")
    }
}
```

## Chapter 23: Best Practices and Idioms

### Prefer Immutability

```kotlin
// Prefer val over var
val name = "Alice"

// Use immutable collections
val list = listOf(1, 2, 3)
val map = mapOf("key" to "value")

// Use data classes with val properties
data class User(val name: String, val age: Int)
```

### Use Data Classes for Models

```kotlin
data class Product(
    val id: Int,
    val name: String,
    val price: Double
)

// Automatic equals, hashCode, toString, copy
```

### Apply Function for Object Configuration

```kotlin
val person = Person().apply {
    name = "Alice"
    age = 25
    email = "alice@example.com"
}
```

### Use Elvis Operator for Defaults

```kotlin
val name = nullableName ?: "Unknown"
val length = text?.length ?: 0
```

### Prefer Expression Bodies

```kotlin
fun double(x: Int): Int = x * 2
fun isEven(x: Int): Boolean = x % 2 == 0
```

### Use Named Arguments for Clarity

```kotlin
createUser(
    name = "Alice",
    age = 25,
    email = "alice@example.com"
)
```

### Leverage Sequence for Large Collections

```kotlin
val result = (1..1_000_000)
    .asSequence()
    .filter { it % 2 == 0 }
    .map { it * 2 }
    .take(10)
    .toList()
```

### Use When Instead of If-Else Chains

```kotlin
val message = when (status) {
    Status.PENDING -> "Waiting"
    Status.APPROVED -> "Approved"
    Status.REJECTED -> "Rejected"
}
```

### Extension Functions for Utility Methods

```kotlin
fun String.isValidEmail(): Boolean {
    return this.contains("@") && this.contains(".")
}
```

### Avoid Non-Null Assertions

```kotlin
// Avoid
val length = name!!.length

// Prefer
val length = name?.length ?: 0
```

## Chapter 24: Testing in Kotlin

### JUnit 5 Setup

```kotlin
// build.gradle.kts
dependencies {
    testImplementation("org.junit.jupiter:junit-jupiter:5.10.0")
    testImplementation("org.assertj:assertj-core:3.24.2")
}

tasks.test {
    useJUnitPlatform()
}
```

### Basic Unit Tests

```kotlin
import org.junit.jupiter.api.Test
import org.junit.jupiter.api.Assertions.*

class CalculatorTest {
    @Test
    fun `addition should return correct sum`() {
        val calculator = Calculator()
        val result = calculator.add(2, 3)
        assertEquals(5, result)
    }

    @Test
    fun `division by zero should throw exception`() {
        val calculator = Calculator()
        assertThrows(ArithmeticException::class.java) {
            calculator.divide(10, 0)
        }
    }
}

class Calculator {
    fun add(a: Int, b: Int) = a + b
    fun divide(a: Int, b: Int) = a / b
}
```

### Testing with MockK

```kotlin
// build.gradle.kts
dependencies {
    testImplementation("io.mockk:mockk:1.13.8")
}
```

```kotlin
import io.mockk.*
import org.junit.jupiter.api.Test
import org.junit.jupiter.api.Assertions.*

interface UserRepository {
    fun findUser(id: Int): User?
}

class UserService(private val repository: UserRepository) {
    fun getUserName(id: Int): String {
        val user = repository.findUser(id)
        return user?.name ?: "Unknown"
    }
}

class UserServiceTest {
    @Test
    fun `getUserName should return user name when user exists`() {
        val mockRepository = mockk<UserRepository>()
        every { mockRepository.findUser(1) } returns User("Alice", 25)

        val service = UserService(mockRepository)
        val result = service.getUserName(1)

        assertEquals("Alice", result)
        verify { mockRepository.findUser(1) }
    }

    @Test
    fun `getUserName should return Unknown when user not found`() {
        val mockRepository = mockk<UserRepository>()
        every { mockRepository.findUser(999) } returns null

        val service = UserService(mockRepository)
        val result = service.getUserName(999)

        assertEquals("Unknown", result)
    }
}
```

### Coroutine Testing

```kotlin
// build.gradle.kts
dependencies {
    testImplementation("org.jetbrains.kotlinx:kotlinx-coroutines-test:1.7.3")
}
```

```kotlin
import kotlinx.coroutines.test.*
import org.junit.jupiter.api.Test
import org.junit.jupiter.api.Assertions.*

class DataFetcher {
    suspend fun fetchData(): String {
        delay(1000L)
        return "Data"
    }
}

class DataFetcherTest {
    @Test
    fun `fetchData should return data after delay`() = runTest {
        val fetcher = DataFetcher()
        val result = fetcher.fetchData()
        assertEquals("Data", result)
    }
}
```

### Exercise 24.1: Test Shopping Cart

Write comprehensive tests for a shopping cart class that adds items, calculates totals, and applies discounts.

```kotlin
data class CartItem(val name: String, val price: Double, val quantity: Int)

class ShoppingCart {
    private val items = mutableListOf<CartItem>()

    fun addItem(name: String, price: Double, quantity: Int) {
        items.add(CartItem(name, price, quantity))
    }

    fun getTotal(): Double = items.sumOf { it.price * it.quantity }

    fun applyDiscount(percentage: Double): Double {
        require(percentage in 0.0..100.0) { "Invalid discount percentage" }
        return getTotal() * (1 - percentage / 100)
    }

    fun getItemCount(): Int = items.size
}

class ShoppingCartTest {
    @Test
    fun `empty cart should have zero total`() {
        val cart = ShoppingCart()
        assertEquals(0.0, cart.getTotal())
    }

    @Test
    fun `adding items should calculate correct total`() {
        val cart = ShoppingCart()
        cart.addItem("Apple", 1.0, 3)
        cart.addItem("Banana", 0.5, 2)
        assertEquals(4.0, cart.getTotal())
    }

    @Test
    fun `applying discount should reduce total`() {
        val cart = ShoppingCart()
        cart.addItem("Item", 100.0, 1)
        val discounted = cart.applyDiscount(10.0)
        assertEquals(90.0, discounted)
    }

    @Test
    fun `invalid discount should throw exception`() {
        val cart = ShoppingCart()
        assertThrows(IllegalArgumentException::class.java) {
            cart.applyDiscount(150.0)
        }
    }
}
```

## Chapter 25: Advanced Topics and Next Steps

### Inline Functions

Improve performance by eliminating lambda overhead:

```kotlin
inline fun <T> measureTime(block: () -> T): T {
    val start = System.currentTimeMillis()
    val result = block()
    val duration = System.currentTimeMillis() - start
    println("Execution time: ${duration}ms")
    return result
}

fun main() {
    val result = measureTime {
        (1..1000000).sum()
    }
}
```

### Contracts

Help the compiler understand function behavior:

```kotlin
import kotlin.contracts.*

inline fun String?.isNullOrEmpty(): Boolean {
    contract {
        returns(false) implies (this@isNullOrEmpty != null)
    }
    return this == null || this.isEmpty()
}
```

### Multiplatform Projects

Share code between JVM, JS, and Native:

```kotlin
// commonMain
expect fun platformName(): String

// jvmMain
actual fun platformName(): String = "JVM"

// jsMain
actual fun platformName(): String = "JavaScript"
```

### Further Learning Resources

To continue your Kotlin journey:

- Official Kotlin documentation at kotlinlang.org provides comprehensive references and guides
- Kotlin Koans interactive exercises help practice language features
- Build real projects using frameworks like Ktor for backend services or Jetpack Compose for Android UI
- Explore Kotlin coroutines flow operators for reactive programming
- Study functional programming patterns in Kotlin
- Contribute to open-source Kotlin projects on GitHub
- Join Kotlin communities on Reddit, Slack, and Stack Overflow

### Final Project: Task Management API

Combine concepts learned to build a complete REST API with database persistence, authentication, and testing:

```kotlin
// Project structure:
// - Models: User, Task, TaskList
// - Database: Exposed setup with proper schemas
// - API: Ktor endpoints for CRUD operations
// - Authentication: JWT tokens
// - Testing: Unit tests for business logic, integration tests for API

// Implementation outline:
// 1. Set up Gradle with Ktor, Exposed, JWT libraries
// 2. Define data models with kotlinx.serialization
// 3. Create database tables and DAOs
// 4. Implement authentication middleware
// 5. Build REST endpoints with proper error handling
// 6. Write comprehensive tests
// 7. Add logging and monitoring
```

## Conclusion

This guide has taken you from Kotlin fundamentals through advanced features used in production environments. You have learned variables, control flow, functions, classes, generics, coroutines, DSL creation, and integration with popular frameworks like Ktor and Room. You understand null safety, functional programming patterns, and idiomatic Kotlin practices.

The exercises throughout this guide provide hands-on experience with real-world scenarios. Continue building projects, exploring the official documentation, and engaging with the Kotlin community. Kotlin's concise syntax, powerful features, and excellent tooling support make it ideal for backend services, Android apps, and cross-platform development.

Start small, practice regularly, and gradually tackle more complex projects. The language's interoperability with Java and extensive library ecosystem ensure you can leverage existing tools while enjoying Kotlin's modern features. Write clean, maintainable, and expressive code by following the idioms and best practices presented here.
