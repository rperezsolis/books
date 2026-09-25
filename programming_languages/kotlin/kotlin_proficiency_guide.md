# Kotlin Programming Language Proficiency Guide

## 1. Introduction

Kotlin is a modern, statically-typed programming language developed by JetBrains that runs on the Java Virtual Machine (JVM). It combines object-oriented and functional programming features, providing a concise, safe, and interoperable alternative to Java.

### Key Characteristics

- **Concise**: Significantly reduces boilerplate code
- **Safe**: Built-in null safety and type system
- **Interoperable**: 100% compatible with Java
- **Expressive**: Modern syntax with powerful features
- **Multi-platform**: Write once, run on JVM, Android, iOS, JavaScript, Native
- **Pragmatic**: Designed for real-world development

### Why Learn Kotlin?

- **Android development**: Official language for Android
- **Server-side**: Spring Boot, Ktor for backend services
- **Multi-platform**: Kotlin Multiplatform for cross-platform code
- **Java interop**: Seamlessly use Java libraries
- **Modern features**: Coroutines, extension functions, data classes
- **Growing ecosystem**: Strong community and tooling support

### Setting Up Kotlin

```bash
# Install using SDKMAN
sdk install kotlin

# Install using Homebrew (macOS)
brew install kotlin

# Verify installation
kotlin -version

# Compile and run
kotlinc hello.kt -include-runtime -d hello.jar
java -jar hello.jar

# Or use Kotlin REPL
kotlinc-jvm
```

### Hello World

```kotlin
// hello.kt
fun main() {
    println("Hello, Kotlin!")
}

// Compile and run:
// kotlinc hello.kt -include-runtime -d hello.jar
// java -jar hello.jar
```

## 2. Core Language Mechanics

### Syntax Fundamentals

```kotlin
// Comments
// Single-line comment
/* Multi-line
   comment */

/**
 * Documentation comment
 * @param name The name parameter
 */

// Statements don't require semicolons
val x = 5
println(x)

// But semicolons are allowed
val y = 10; println(y)

// Code blocks
if (true) {
    println("Block")
}

// Single-expression functions
fun square(x: Int) = x * x
```

### Variables and Constants

```kotlin
fun variablesDemo() {
    // val - immutable (read-only) reference
    val name = "Alice"
    val age = 30
    // name = "Bob" // ERROR: Val cannot be reassigned
    
    // var - mutable reference
    var count = 0
    count = 1 // OK
    
    // Explicit types
    val city: String = "New York"
    val population: Int = 8000000
    val temperature: Double = 72.5
    val isCapital: Boolean = false
    
    // Type inference
    val inferred = "Hello" // Type: String
    val number = 42        // Type: Int
    
    // Late initialization
    lateinit var description: String
    description = "Set later"
    println(description)
    
    // Lazy initialization
    val lazyValue: String by lazy {
        println("Computing...")
        "Computed value"
    }
    println(lazyValue) // Computed on first access
    
    // Const - compile-time constant (top-level or object)
    // const val PI = 3.14159
}

// Top-level constants
const val APP_NAME = "MyApp"
const val MAX_COUNT = 100
```

### Data Types

```kotlin
fun dataTypesDemo() {
    // Numbers
    val byte: Byte = 127
    val short: Short = 32767
    val int: Int = 2147483647
    val long: Long = 9223372036854775807L
    
    val float: Float = 3.14f
    val double: Double = 3.14159
    
    // Underscores in numbers
    val million = 1_000_000
    val creditCard = 1234_5678_9012_3456L
    val bytes = 0xFF_EC_DE_5E
    
    // Type conversions
    val i: Int = 42
    val l: Long = i.toLong()
    val d: Double = i.toDouble()
    val s: String = i.toString()
    
    // Characters
    val char: Char = 'A'
    val digit: Char = '5'
    val unicode: Char = '\u0041' // 'A'
    
    // Booleans
    val isTrue: Boolean = true
    val isFalse: Boolean = false
    
    // Strings
    val singleLine = "Hello, Kotlin!"
    val multiLine = """
        |Line 1
        |Line 2
        |Line 3
    """.trimMargin()
    
    // String templates
    val name = "Alice"
    val age = 30
    println("$name is $age years old")
    println("Next year: ${age + 1}")
    
    // Raw strings
    val text = """
        {
            "name": "Alice",
            "age": 30
        }
    """.trimIndent()
    
    // String methods
    val str = "Hello"
    println(str.length)
    println(str.uppercase())
    println(str.lowercase())
    println(str.substring(0, 3))
    println(str.startsWith("He"))
    println(str.endsWith("lo"))
    println(str.contains("ell"))
    
    // Arrays
    val array = arrayOf(1, 2, 3, 4, 5)
    val intArray = intArrayOf(1, 2, 3) // Primitive array
    val nullableArray = arrayOfNulls<String>(5)
    
    // Ranges
    val range = 1..10
    val range2 = 1 until 10 // Excludes 10
    val range3 = 10 downTo 1
    val range4 = 1..10 step 2
}
```

### Null Safety

```kotlin
fun nullSafetyDemo() {
    // Non-nullable by default
    var name: String = "Alice"
    // name = null // ERROR: Null can not be a value of a non-null type
    
    // Nullable types
    var nullableName: String? = null
    nullableName = "Bob" // OK
    nullableName = null  // OK
    
    // Safe call operator ?.
    val length = nullableName?.length
    println(length) // null if nullableName is null
    
    // Elvis operator ?:
    val displayName = nullableName ?: "Guest"
    val len = nullableName?.length ?: 0
    
    // Safe cast as?
    val obj: Any = "Hello"
    val str: String? = obj as? String
    val num: Int? = obj as? Int // null if cast fails
    
    // Not-null assertion !!
    val name2 = nullableName!!.uppercase() // Throws NPE if null
    
    // Let function with safe call
    nullableName?.let {
        println("Name is $it")
        println("Length is ${it.length}")
    }
    
    // Checking for null
    if (nullableName != null) {
        // Smart cast: nullableName is String here
        println(nullableName.length)
    }
    
    // Nullable collections
    val list: List<String?> = listOf("A", null, "B")
    val list2: List<String>? = null
    val list3: List<String?>? = null
    
    // Safe iteration
    list3?.forEach { item ->
        item?.let { println(it) }
    }
}
```

### Operators

```kotlin
fun operatorsDemo() {
    // Arithmetic
    println(5 + 3)    // 8
    println(5 - 3)    // 2
    println(5 * 3)    // 15
    println(5 / 3)    // 1 (integer division)
    println(5 / 3.0)  // 1.666...
    println(5 % 3)    // 2
    
    // Increment/Decrement
    var a = 5
    println(++a)      // 6 (pre-increment)
    println(a++)      // 6 (post-increment)
    println(a)        // 7
    
    // Assignment
    var x = 10
    x += 5  // x = x + 5
    x -= 3  // x = x - 3
    x *= 2  // x = x * 2
    x /= 4  // x = x / 4
    x %= 3  // x = x % 3
    
    // Comparison
    println(5 == 3)   // false
    println(5 != 3)   // true
    println(5 > 3)    // true
    println(5 < 3)    // false
    println(5 >= 3)   // true
    println(5 <= 3)   // false
    
    // Logical
    println(true && false)  // false
    println(true || false)  // true
    println(!true)          // false
    
    // In operator
    val range = 1..10
    println(5 in range)     // true
    println(15 !in range)   // true
    
    val list = listOf(1, 2, 3)
    println(2 in list)      // true
    
    // Is operator (type check)
    val obj: Any = "Hello"
    if (obj is String) {
        // Smart cast: obj is String here
        println(obj.length)
    }
    
    if (obj !is Int) {
        println("Not an Int")
    }
    
    // Bitwise operations
    val bits1 = 0b1010
    val bits2 = 0b1100
    
    println(bits1 and bits2)  // 0b1000
    println(bits1 or bits2)   // 0b1110
    println(bits1 xor bits2)  // 0b0110
    println(bits1.inv())      // Bitwise NOT
    println(bits1 shl 1)      // Left shift
    println(bits1 shr 1)      // Right shift
    println(bits1 ushr 1)     // Unsigned right shift
    
    // Equality
    val a1 = "Hello"
    val a2 = "Hello"
    println(a1 == a2)         // true (structural equality)
    println(a1 === a2)        // May be true (referential equality)
    
    val list1 = listOf(1, 2, 3)
    val list2 = listOf(1, 2, 3)
    println(list1 == list2)   // true
    println(list1 === list2)  // false (different objects)
}
```

### Type System

```kotlin
fun typeSystemDemo() {
    // Type inference
    val str = "Hello"      // String
    val num = 42           // Int
    val dec = 3.14         // Double
    
    // Explicit types
    val name: String = "Alice"
    val age: Int = 30
    
    // Any type (root of type hierarchy)
    val any: Any = "Can be anything"
    
    // Unit type (like void)
    fun doSomething(): Unit {
        println("Doing something")
    }
    
    // Nothing type (never returns)
    fun fail(): Nothing {
        throw Exception("Failure")
    }
    
    // Smart casts
    fun getLength(obj: Any): Int {
        if (obj is String) {
            // obj is automatically cast to String
            return obj.length
        }
        return 0
    }
    
    // When with smart casts
    fun describe(obj: Any): String = when (obj) {
        is String -> "String of length ${obj.length}"
        is Int -> "Int: $obj"
        is List<*> -> "List of size ${obj.size}"
        else -> "Unknown type"
    }
    
    // Type aliases
    typealias UserMap = Map<String, User>
    typealias StringList = List<String>
    typealias Predicate<T> = (T) -> Boolean
    
    // Generic functions
    fun <T> singletonList(item: T): List<T> {
        return listOf(item)
    }
    
    val list = singletonList(42)
    val list2 = singletonList("Hello")
    
    // Generic constraints
    fun <T : Comparable<T>> max(a: T, b: T): T {
        return if (a > b) a else b
    }
    
    println(max(5, 10))
    println(max("apple", "banana"))
}

data class User(val name: String, val age: Int)
```

## 3. Control Flow

### Conditional Statements

```kotlin
fun conditionalsDemo() {
    val age = 20
    
    // If-else
    if (age < 18) {
        println("Minor")
    } else if (age < 65) {
        println("Adult")
    } else {
        println("Senior")
    }
    
    // If as expression
    val status = if (age >= 18) "Adult" else "Minor"
    
    val max = if (a > b) {
        println("Choose a")
        a
    } else {
        println("Choose b")
        b
    }
    
    // When statement (like switch)
    val grade = 'B'
    when (grade) {
        'A' -> println("Excellent")
        'B' -> println("Good")
        'C' -> println("Average")
        'D', 'F' -> println("Poor")
        else -> println("Invalid grade")
    }
    
    // When as expression
    val result = when (grade) {
        'A' -> "Excellent"
        'B' -> "Good"
        'C' -> "Average"
        else -> "Other"
    }
    
    // When with conditions
    val x = 15
    when {
        x < 0 -> println("Negative")
        x == 0 -> println("Zero")
        x > 0 -> println("Positive")
    }
    
    // When with ranges
    val score = 85
    when (score) {
        in 90..100 -> println("A")
        in 80..89 -> println("B")
        in 70..79 -> println("C")
        in 60..69 -> println("D")
        else -> println("F")
    }
    
    // When with type checks
    fun describe(obj: Any): String = when (obj) {
        is String -> "String of length ${obj.length}"
        is Int -> "Integer: $obj"
        is Boolean -> "Boolean: $obj"
        is List<*> -> "List of size ${obj.size}"
        else -> "Unknown"
    }
    
    // When without argument
    val temperature = 25
    when {
        temperature < 0 -> println("Freezing")
        temperature < 20 -> println("Cold")
        temperature < 30 -> println("Warm")
        else -> println("Hot")
    }
}
```

### Loops

```kotlin
fun loopsDemo() {
    // For loop with ranges
    for (i in 1..5) {
        println(i)
    }
    
    // For loop with until (excludes end)
    for (i in 1 until 5) {
        println(i) // 1, 2, 3, 4
    }
    
    // For loop with downTo
    for (i in 5 downTo 1) {
        println(i)
    }
    
    // For loop with step
    for (i in 1..10 step 2) {
        println(i) // 1, 3, 5, 7, 9
    }
    
    // For loop with collections
    val fruits = listOf("apple", "banana", "orange")
    for (fruit in fruits) {
        println(fruit)
    }
    
    // For loop with indices
    for (i in fruits.indices) {
        println("$i: ${fruits[i]}")
    }
    
    // For loop with index
    for ((index, value) in fruits.withIndex()) {
        println("$index: $value")
    }
    
    // While loop
    var count = 0
    while (count < 5) {
        println(count)
        count++
    }
    
    // Do-while loop
    var num = 0
    do {
        println(num)
        num++
    } while (num < 5)
    
    // Break and continue
    for (i in 1..10) {
        if (i == 3) continue
        if (i == 7) break
        println(i)
    }
    
    // Labeled break
    outer@ for (i in 1..3) {
        for (j in 1..3) {
            if (i == 2 && j == 2) break@outer
            println("$i, $j")
        }
    }
    
    // forEach
    fruits.forEach { fruit ->
        println(fruit)
    }
    
    // forEachIndexed
    fruits.forEachIndexed { index, fruit ->
        println("$index: $fruit")
    }
    
    // repeat
    repeat(3) {
        println("Iteration $it")
    }
}
```

### Exception Handling

```kotlin
// Custom exceptions
class InvalidAgeException(message: String) : Exception(message)
class ValidationException(val field: String, message: String) : Exception(message)

fun exceptionHandlingDemo() {
    // Basic try-catch
    try {
        val result = 12 / 0
        println(result)
    } catch (e: ArithmeticException) {
        println("Cannot divide by zero: ${e.message}")
    }
    
    // Multiple catch blocks
    try {
        // Some operation
        throw NumberFormatException("Invalid number")
    } catch (e: NumberFormatException) {
        println("Number format error: ${e.message}")
    } catch (e: IllegalArgumentException) {
        println("Illegal argument: ${e.message}")
    } catch (e: Exception) {
        println("General error: ${e.message}")
    }
    
    // Finally block
    try {
        println("Attempting operation")
        throw Exception("Operation failed")
    } catch (e: Exception) {
        println("Caught: ${e.message}")
    } finally {
        println("Cleanup code runs regardless")
    }
    
    // Try as expression
    val number = try {
        "42".toInt()
    } catch (e: NumberFormatException) {
        -1
    }
    
    // Nothing type for functions that always throw
    fun fail(message: String): Nothing {
        throw IllegalStateException(message)
    }
    
    // Elvis operator with throw
    val name: String? = null
    val displayName = name ?: throw IllegalArgumentException("Name required")
    
    // requireNotNull and checkNotNull
    val value: String? = "Hello"
    val notNull = requireNotNull(value) { "Value must not be null" }
    
    // require and check
    fun setAge(age: Int) {
        require(age >= 0) { "Age must be non-negative" }
        check(age < 150) { "Age must be realistic" }
    }
    
    // Custom exceptions
    try {
        validateAge(-5)
    } catch (e: InvalidAgeException) {
        println(e.message)
    }
}

fun validateAge(age: Int) {
    if (age < 0) {
        throw InvalidAgeException("Age cannot be negative: $age")
    }
}

// Result type for error handling
fun divide(a: Int, b: Int): Result<Int> = runCatching {
    if (b == 0) throw ArithmeticException("Division by zero")
    a / b
}

fun resultDemo() {
    val result = divide(10, 2)
    
    result.onSuccess { value ->
        println("Result: $value")
    }.onFailure { error ->
        println("Error: ${error.message}")
    }
    
    // Get or default
    val value = divide(10, 0).getOrDefault(-1)
    
    // Get or null
    val value2 = divide(10, 0).getOrNull()
    
    // Get or throw
    val value3 = divide(10, 2).getOrThrow()
}
```

## 4. Functions and Code Organization

### Function Basics

```kotlin
// Basic function
fun add(a: Int, b: Int): Int {
    return a + b
}

// Single-expression function
fun multiply(a: Int, b: Int) = a * b

// Function with no return value
fun greet(name: String) {
    println("Hello, $name!")
}

fun greet2(name: String): Unit {
    println("Hello, $name!")
}

// Default parameters
fun power(base: Int, exponent: Int = 2): Int {
    var result = 1
    repeat(exponent) {
        result *= base
    }
    return result
}

// Named arguments
fun createUser(
    name: String,
    age: Int,
    email: String = "",
    phone: String? = null
) {
    println("Name: $name")
    println("Age: $age")
    if (email.isNotEmpty()) println("Email: $email")
    if (phone != null) println("Phone: $phone")
}

fun functionsDemo() {
    // Calling functions
    println(add(5, 3))
    println(multiply(4, 7))
    greet("Alice")
    
    // Default parameters
    println(power(2))      // Uses default exponent 2
    println(power(2, 3))   // Explicit exponent
    
    // Named arguments
    createUser(name = "Alice", age = 30)
    createUser(
        name = "Bob",
        age = 25,
        email = "bob@example.com",
        phone = "555-1234"
    )
    
    // Mixed positional and named
    createUser("Charlie", 35, email = "charlie@example.com")
}

// Vararg parameters
fun sum(vararg numbers: Int): Int {
    return numbers.sum()
}

fun printAll(vararg messages: String) {
    for (message in messages) {
        println(message)
    }
}

fun varargDemo() {
    println(sum(1, 2, 3, 4, 5))
    
    val numbers = intArrayOf(1, 2, 3, 4, 5)
    println(sum(*numbers)) // Spread operator
    
    printAll("Hello", "World", "Kotlin")
}

// Infix functions
infix fun Int.times(str: String) = str.repeat(this)

fun infixDemo() {
    println(3 times "Hello ") // HelloHelloHello
    println(3.times("World ")) // Same as above
}

// Operator overloading
data class Point(val x: Int, val y: Int) {
    operator fun plus(other: Point) = Point(x + other.x, y + other.y)
    operator fun minus(other: Point) = Point(x - other.x, y - other.y)
    operator fun times(scalar: Int) = Point(x * scalar, y * scalar)
}

fun operatorDemo() {
    val p1 = Point(1, 2)
    val p2 = Point(3, 4)
    
    println(p1 + p2)  // Point(4, 6)
    println(p1 - p2)  // Point(-2, -2)
    println(p1 * 2)   // Point(2, 4)
}
```

### Higher-Order Functions

```kotlin
// Function as parameter
fun operate(a: Int, b: Int, operation: (Int, Int) -> Int): Int {
    return operation(a, b)
}

// Function returning function
fun makeAdder(addBy: Int): (Int) -> Int {
    return { value -> value + addBy }
}

// Type aliases for function types
typealias Predicate<T> = (T) -> Boolean
typealias Transformer<T, R> = (T) -> R

fun higherOrderDemo() {
    // Pass function as argument
    val sum = operate(5, 3) { a, b -> a + b }
    val product = operate(5, 3) { a, b -> a * b }
    
    println(sum)      // 8
    println(product)  // 15
    
    // Return function
    val add5 = makeAdder(5)
    println(add5(10)) // 15
    println(add5(20)) // 25
    
    // Function references
    val numbers = listOf(1, 2, 3, 4, 5)
    
    // Lambda
    val doubled = numbers.map { it * 2 }
    
    // Function reference
    val strings = numbers.map(Int::toString)
    
    // Collection operations
    val evens = numbers.filter { it % 2 == 0 }
    val sum = numbers.reduce { acc, n -> acc + n }
    val product = numbers.fold(1) { acc, n -> acc * n }
    
    // Using typealias
    val isEven: Predicate<Int> = { it % 2 == 0 }
    val toUpperCase: Transformer<String, String> = { it.uppercase() }
    
    println(numbers.filter(isEven))
    println(listOf("hello", "world").map(toUpperCase))
}

// Lambda with receiver
fun buildString(builder: StringBuilder.() -> Unit): String {
    val sb = StringBuilder()
    sb.builder()
    return sb.toString()
}

fun lambdaReceiverDemo() {
    val result = buildString {
        append("Hello")
        append(" ")
        append("World")
    }
    println(result)
}
```

### Extension Functions

```kotlin
// Extension function
fun String.isPalindrome(): Boolean {
    return this == this.reversed()
}

fun Int.isEven() = this % 2 == 0

fun Int.squared() = this * this

// Extension with parameters
fun String.repeat(times: Int): String {
    return this.repeat(times)
}

// Nullable receiver
fun String?.orEmpty(): String {
    return this ?: ""
}

fun extensionDemo() {
    println("racecar".isPalindrome())  // true
    println("hello".isPalindrome())    // false
    
    println(4.isEven())     // true
    println(5.isEven())     // false
    
    println(5.squared())    // 25
    
    val nullString: String? = null
    println(nullString.orEmpty()) // ""
}

// Extension properties
val String.lastChar: Char
    get() = this[length - 1]

val <T> List<T>.secondOrNull: T?
    get() = if (size >= 2) this[1] else null

// Generic extensions
fun <T> List<T>.second(): T {
    if (size < 2) throw NoSuchElementException()
    return this[1]
}

fun <T> List<T>.swap(index1: Int, index2: Int): List<T> {
    val result = this.toMutableList()
    val temp = result[index1]
    result[index1] = result[index2]
    result[index2] = temp
    return result
}
```

### Scope Functions

```kotlin
fun scopeFunctionsDemo() {
    // let - call functions on nullable objects, transform value
    val name: String? = "Alice"
    name?.let {
        println("Name is $it")
        println("Length is ${it.length}")
    }
    
    val length = name?.let { it.length } ?: 0
    
    // also - additional operations, return object
    val numbers = mutableListOf(1, 2, 3)
        .also { println("Before: $it") }
        .also { it.add(4) }
        .also { println("After: $it") }
    
    // apply - configure object, return object
    val person = Person("", 0).apply {
        name = "Alice"
        age = 30
    }
    
    val stringBuilder = StringBuilder().apply {
        append("Hello")
        append(" ")
        append("World")
    }
    
    // run - run code block, return result
    val result = run {
        val a = 5
        val b = 3
        a + b
    }
    
    val connection = DatabaseConnection().run {
        connect()
        query("SELECT * FROM users")
    }
    
    // with - call multiple methods, return result
    val text = with(StringBuilder()) {
        append("Line 1\n")
        append("Line 2\n")
        append("Line 3")
        toString()
    }
    
    // takeIf and takeUnless
    val positive = 42.takeIf { it > 0 }  // 42
    val negative = -5.takeIf { it > 0 }   // null
    
    val even = 4.takeUnless { it % 2 != 0 } // 4
    val odd = 5.takeUnless { it % 2 != 0 }  // null
}

data class Person(var name: String, var age: Int)

class DatabaseConnection {
    fun connect() {
        println("Connected")
    }
    
    fun query(sql: String): List<String> {
        println("Executing: $sql")
        return listOf("Result 1", "Result 2")
    }
}
```

### Coroutines and Async

```kotlin
import kotlinx.coroutines.*

suspend fun fetchUser(id: Int): String {
    delay(1000) // Simulate network delay
    return "User $id"
}

suspend fun fetchPosts(userId: Int): List<String> {
    delay(500)
    return listOf("Post 1", "Post 2", "Post 3")
}

fun coroutinesDemo() = runBlocking {
    // Launch coroutine
    launch {
        delay(1000)
        println("World!")
    }
    println("Hello")
    
    // Async/await
    val user = async { fetchUser(1) }
    val posts = async { fetchPosts(1) }
    
    println("User: ${user.await()}")
    println("Posts: ${posts.await()}")
    
    // Parallel execution
    val results = listOf(1, 2, 3).map { id ->
        async { fetchUser(id) }
    }.awaitAll()
    
    println(results)
}

// Flow (reactive streams)
fun numbersFlow() = flow {
    for (i in 1..5) {
        delay(100)
        emit(i)
    }
}

fun flowDemo() = runBlocking {
    numbersFlow()
        .map { it * 2 }
        .filter { it > 5 }
        .collect { value ->
            println(value)
        }
}
```

## 5. Data Structures

### Lists

```kotlin
fun listsDemo() {
    // Read-only list
    val list = listOf(1, 2, 3, 4, 5)
    val strings = listOf("a", "b", "c")
    val empty = emptyList<Int>()
    
    // Mutable list
    val mutableList = mutableListOf(1, 2, 3)
    mutableList.add(4)
    mutableList.add(0, 0)
    mutableList.remove(2)
    mutableList.removeAt(0)
    mutableList[1] = 10
    
    // ArrayList
    val arrayList = arrayListOf(1, 2, 3)
    
    // Access
    println(list[0])           // First element
    println(list.first())      // First element
    println(list.last())       // Last element
    println(list.firstOrNull())
    println(list.lastOrNull())
    println(list.getOrNull(10))
    println(list.getOrElse(10) { 0 })
    
    // Properties
    println(list.size)
    println(list.isEmpty())
    println(list.isNotEmpty())
    println(list.indices)
    
    // Sublist
    val sublist = list.subList(1, 4)
    
    // Searching
    println(list.contains(3))
    println(3 in list)
    println(list.indexOf(3))
    println(list.lastIndexOf(2))
    println(list.find { it > 3 })
    println(list.findLast { it > 3 })
    
    // Transformation
    val doubled = list.map { it * 2 }
    val evens = list.filter { it % 2 == 0 }
    val sum = list.reduce { acc, n -> acc + n }
    val product = list.fold(1) { acc, n -> acc * n }
    
    // Flattening
    val nested = listOf(listOf(1, 2), listOf(3, 4), listOf(5))
    val flattened = nested.flatten()
    val flatMapped = nested.flatMap { it.map { n -> n * 2 } }
    
    // Chunking and windowing
    val chunked = list.chunked(2)
    val windowed = list.windowed(3)
    
    // Sorting
    val unsorted = listOf(3, 1, 4, 1, 5, 9, 2, 6)
    val sorted = unsorted.sorted()
    val sortedDesc = unsorted.sortedDescending()
    val sortedBy = listOf("banana", "apple", "cherry").sortedBy { it.length }
    
    // Reversing
    val reversed = list.reversed()
    
    // Distinct
    val withDuplicates = listOf(1, 2, 2, 3, 3, 3)
    val distinct = withDuplicates.distinct()
    val distinctBy = listOf("a", "ab", "abc", "b").distinctBy { it.length }
    
    // Grouping
    val grouped = list.groupBy { it % 2 == 0 }
    
    // Partitioning
    val (evens2, odds) = list.partition { it % 2 == 0 }
    
    // Zipping
    val list1 = listOf(1, 2, 3)
    val list2 = listOf("a", "b", "c")
    val zipped = list1.zip(list2)
    
    // Take and drop
    println(list.take(3))
    println(list.takeLast(3))
    println(list.takeWhile { it < 4 })
    println(list.drop(2))
    println(list.dropLast(2))
    println(list.dropWhile { it < 3 })
    
    // Any, all, none
    println(list.any { it > 3 })
    println(list.all { it > 0 })
    println(list.none { it < 0 })
    
    // Min, max, sum, average
    println(list.minOrNull())
    println(list.maxOrNull())
    println(list.sum())
    println(list.average())
}
```

### Sets

```kotlin
fun setsDemo() {
    // Read-only set
    val set = setOf(1, 2, 3, 3, 3) // {1, 2, 3}
    val strings = setOf("a", "b", "c")
    val empty = emptySet<Int>()
    
    // Mutable set
    val mutableSet = mutableSetOf(1, 2, 3)
    mutableSet.add(4)
    mutableSet.add(3) // No effect (already exists)
    mutableSet.remove(2)
    mutableSet.addAll(listOf(5, 6))
    
    // HashSet and LinkedHashSet
    val hashSet = hashSetOf(1, 2, 3)
    val linkedHashSet = linkedSetOf(1, 2, 3) // Maintains order
    
    // Properties
    println(set.size)
    println(set.isEmpty())
    println(set.contains(2))
    println(2 in set)
    
    // Set operations
    val a = setOf(1, 2, 3, 4)
    val b = setOf(3, 4, 5, 6)
    
    // Union
    println(a union b)         // {1, 2, 3, 4, 5, 6}
    println(a + b)             // Same as union
    
    // Intersection
    println(a intersect b)     // {3, 4}
    
    // Difference
    println(a subtract b)      // {1, 2}
    println(a - b)             // Same as subtract
    
    // Convert
    val listFromSet = set.toList()
    val setFromList = listOf(1, 2, 2, 3).toSet()
    
    // Remove duplicates
    val numbers = listOf(1, 2, 2, 3, 3, 3, 4, 5, 5)
    val unique = numbers.toSet()
}
```

### Maps

```kotlin
fun mapsDemo() {
    // Read-only map
    val map = mapOf("a" to 1, "b" to 2, "c" to 3)
    val map2 = mapOf(Pair("x", 10), Pair("y", 20))
    val empty = emptyMap<String, Int>()
    
    // Mutable map
    val mutableMap = mutableMapOf("a" to 1, "b" to 2)
    mutableMap["c"] = 3
    mutableMap.put("d", 4)
    mutableMap.remove("a")
    mutableMap.putAll(mapOf("e" to 5, "f" to 6))
    
    // HashMap and LinkedHashMap
    val hashMap = hashMapOf("a" to 1, "b" to 2)
    val linkedHashMap = linkedMapOf("a" to 1, "b" to 2) // Maintains order
    
    // Access
    println(map["a"])                  // 1
    println(map.get("a"))              // 1
    println(map.getOrDefault("z", 0))  // 0
    println(map.getOrElse("z") { 0 })  // 0
    println(map.getValue("a"))         // 1 (throws if missing)
    
    // Properties
    println(map.size)
    println(map.isEmpty())
    println(map.containsKey("a"))
    println("a" in map)
    println(map.containsValue(1))
    println(map.keys)
    println(map.values)
    println(map.entries)
    
    // Iteration
    for ((key, value) in map) {
        println("$key -> $value")
    }
    
    map.forEach { (key, value) ->
        println("$key -> $value")
    }
    
    for (entry in map.entries) {
        println("${entry.key} -> ${entry.value}")
    }
    
    // Transformation
    val doubled = map.mapValues { (_, value) -> value * 2 }
    val uppercased = map.mapKeys { (key, _) -> key.uppercase() }
    
    val filtered = map.filter { (_, value) -> value > 1 }
    val filteredKeys = map.filterKeys { it != "a" }
    val filteredValues = map.filterValues { it > 1 }
    
    // Convert
    val list = map.toList() // List of Pairs
    val mapFromList = list.toMap()
    
    // Merge maps
    val map3 = mapOf("a" to 1, "b" to 2)
    val map4 = mapOf("b" to 20, "c" to 3)
    val merged = map3 + map4 // Later values override
    
    // Associate
    val numbers = listOf(1, 2, 3, 4, 5)
    val numberMap = numbers.associateWith { it * it }
    val stringMap = numbers.associateBy { "num_$it" }
    
    // Group by
    val words = listOf("apple", "banana", "apricot", "berry")
    val grouped = words.groupBy { it.first() }
}
```

### Arrays

```kotlin
fun arraysDemo() {
    // Array creation
    val array = arrayOf(1, 2, 3, 4, 5)
    val nullArray = arrayOfNulls<String>(5)
    val generatedArray = Array(5) { i -> i * 2 }
    
    // Primitive arrays (no boxing)
    val intArray = intArrayOf(1, 2, 3)
    val longArray = longArrayOf(1L, 2L, 3L)
    val doubleArray = doubleArrayOf(1.0, 2.0, 3.0)
    val booleanArray = booleanArrayOf(true, false, true)
    val charArray = charArrayOf('a', 'b', 'c')
    
    // Access
    println(array[0])
    println(array.first())
    println(array.last())
    println(array.get(0))
    println(array.getOrNull(10))
    
    // Modify
    array[0] = 10
    array.set(1, 20)
    
    // Properties
    println(array.size)
    println(array.isEmpty())
    println(array.isNotEmpty())
    println(array.indices)
    
    // Iteration
    for (element in array) {
        println(element)
    }
    
    for (i in array.indices) {
        println("$i: ${array[i]}")
    }
    
    array.forEach { println(it) }
    array.forEachIndexed { index, value ->
        println("$index: $value")
    }
    
    // Convert
    val list = array.toList()
    val set = array.toSet()
    val arrayFromList = list.toTypedArray()
    val intArrayFromList = list.toIntArray()
    
    // Operations (same as lists)
    val mapped = array.map { it * 2 }
    val filtered = array.filter { it > 2 }
    val sum = array.sum()
    
    // Multi-dimensional arrays
    val matrix = Array(3) { IntArray(3) }
    matrix[0][0] = 1
    matrix[1][1] = 5
    matrix[2][2] = 9
    
    // 2D array creation
    val grid = arrayOf(
        intArrayOf(1, 2, 3),
        intArrayOf(4, 5, 6),
        intArrayOf(7, 8, 9)
    )
}
```

### Sequences

```kotlin
fun sequencesDemo() {
    // Lazy evaluation
    val sequence = sequenceOf(1, 2, 3, 4, 5)
    
    // Generate sequence
    val generated = generateSequence(1) { it + 1 }
        .take(10)
        .toList()
    
    // From collection
    val list = listOf(1, 2, 3, 4, 5)
    val seq = list.asSequence()
    
    // Lazy operations
    val result = seq
        .filter { 
            println("Filter: $it")
            it % 2 == 0
        }
        .map {
            println("Map: $it")
            it * 2
        }
        .toList() // Terminal operation triggers evaluation
    
    // Infinite sequences
    val fibonacci = generateSequence(Pair(0, 1)) { (a, b) ->
        Pair(b, a + b)
    }.map { it.first }
    
    val first10Fib = fibonacci.take(10).toList()
    println(first10Fib)
    
    // File lines as sequence
    // java.io.File("data.txt").useLines { lines ->
    //     lines.filter { it.isNotBlank() }
    //          .map { it.trim() }
    //          .forEach { println(it) }
    // }
}
```

## 6. Object-Oriented Programming

### Classes and Objects

```kotlin
// Basic class
class Person(val name: String, var age: Int) {
    // Secondary constructor
    constructor(name: String) : this(name, 0)
    
    // Init block
    init {
        println("Person created: $name")
    }
    
    // Methods
    fun greet() {
        println("Hello, I'm $name")
    }
    
    fun haveBirthday() {
        age++
    }
}

// Properties with custom getters/setters
class Rectangle(val width: Int, val height: Int) {
    val area: Int
        get() = width * height
    
    val isSquare: Boolean
        get() = width == height
    
    var scale: Int = 1
        set(value) {
            if (value > 0) {
                field = value
            }
        }
}

// Data classes
data class User(
    val id: Int,
    val name: String,
    val email: String
)

fun dataClassDemo() {
    val user = User(1, "Alice", "alice@example.com")
    
    // Auto-generated methods
    println(user)  // toString()
    
    val user2 = user.copy(name = "Bob")  // copy()
    
    val (id, name, email) = user  // componentN()
    
    println(user == user2)  // equals()
    println(user.hashCode())  // hashCode()
}

// Object declarations (singletons)
object Database {
    private val connections = mutableListOf<String>()
    
    fun connect(url: String) {
        connections.add(url)
        println("Connected to $url")
    }
    
    fun getConnectionCount() = connections.size
}

// Companion objects
class MyClass {
    companion object {
        const val CONSTANT = 42
        
        fun create(): MyClass {
            return MyClass()
        }
    }
}

// Object expressions (anonymous objects)
fun objectExpressionDemo() {
    val clickHandler = object {
        fun onClick() {
            println("Clicked!")
        }
    }
    
    clickHandler.onClick()
}

// Sealed classes
sealed class Result {
    data class Success(val data: String) : Result()
    data class Error(val message: String) : Result()
    object Loading : Result()
}

fun handleResult(result: Result) = when (result) {
    is Result.Success -> println("Data: ${result.data}")
    is Result.Error -> println("Error: ${result.message}")
    is Result.Loading -> println("Loading...")
}

// Enum classes
enum class Color(val rgb: Int) {
    RED(0xFF0000),
    GREEN(0x00FF00),
    BLUE(0x0000FF);
    
    fun printColor() {
        println("$name: #${rgb.toString(16)}")
    }
}

enum class Direction {
    NORTH, SOUTH, EAST, WEST
}
```

### Inheritance

```kotlin
// Open class (can be inherited)
open class Animal(val name: String) {
    open fun makeSound() {
        println("Some generic sound")
    }
    
    fun eat() {
        println("$name is eating")
    }
}

// Derived class
class Dog(name: String, val breed: String) : Animal(name) {
    override fun makeSound() {
        println("$name barks: Woof!")
    }
    
    fun fetch() {
        println("$name is fetching")
    }
}

class Cat(name: String, val isIndoor: Boolean) : Animal(name) {
    override fun makeSound() {
        println("$name meows")
    }
    
    fun scratch() {
        println("$name is scratching")
    }
}

// Abstract classes
abstract class Shape {
    abstract val name: String
    abstract fun area(): Double
    abstract fun perimeter(): Double
    
    fun display() {
        println("$name - Area: ${area()}, Perimeter: ${perimeter()}")
    }
}

class Circle(val radius: Double) : Shape() {
    override val name = "Circle"
    
    override fun area() = Math.PI * radius * radius
    override fun perimeter() = 2 * Math.PI * radius
}

class Rectangle2(val width: Double, val height: Double) : Shape() {
    override val name = "Rectangle"
    
    override fun area() = width * height
    override fun perimeter() = 2 * (width + height)
}

// Calling super
open class Parent {
    open fun greet() {
        println("Hello from Parent")
    }
}

class Child : Parent() {
    override fun greet() {
        super.greet()
        println("Hello from Child")
    }
}
```

### Interfaces

```kotlin
// Interface
interface Drawable {
    fun draw()
    
    // Default implementation
    fun describe() {
        println("This is drawable")
    }
}

interface Movable {
    fun move(x: Int, y: Int)
    var position: Pair<Int, Int>
}

// Implementing multiple interfaces
class GameObject(override var position: Pair<Int, Int> = Pair(0, 0)) : Drawable, Movable {
    override fun draw() {
        println("Drawing at $position")
    }
    
    override fun move(x: Int, y: Int) {
        position = Pair(x, y)
        println("Moved to $position")
    }
}

// Interface with properties
interface Named {
    val name: String
    val fullName: String
        get() = "Named: $name"
}

class PersonWithInterface(override val name: String) : Named

// Functional (SAM) interfaces
fun interface Clickable {
    fun onClick()
}

fun setClickListener(clickable: Clickable) {
    clickable.onClick()
}

fun samDemo() {
    // Lambda conversion
    setClickListener {
        println("Clicked!")
    }
}
```

### Delegation

```kotlin
// Class delegation
interface Base {
    fun print()
    fun getMessage(): String
}

class BaseImpl(val x: Int) : Base {
    override fun print() {
        println("BaseImpl: $x")
    }
    
    override fun getMessage() = "Message from BaseImpl"
}

// Delegate to another object
class Derived(b: Base) : Base by b {
    // Can override if needed
    override fun getMessage() = "Message from Derived"
}

fun delegationDemo() {
    val base = BaseImpl(10)
    val derived = Derived(base)
    
    derived.print()  // Delegated to base
    println(derived.getMessage())  // Overridden
}

// Property delegation
class Example {
    // Lazy
    val lazyValue: String by lazy {
        println("Computing...")
        "Hello"
    }
    
    // Observable
    var name: String by Delegates.observable("Initial") { prop, old, new ->
        println("$old -> $new")
    }
    
    // Vetoable
    var age: Int by Delegates.vetoable(0) { prop, old, new ->
        new >= 0  // Only accept non-negative values
    }
}

// Custom delegate
class StringDelegate {
    operator fun getValue(thisRef: Any?, property: KProperty<*>): String {
        return "$thisRef, thank you for delegating '${property.name}' to me!"
    }
    
    operator fun setValue(thisRef: Any?, property: KProperty<*>, value: String) {
        println("$value has been assigned to '${property.name}' in $thisRef.")
    }
}

class CustomDelegationExample {
    var text: String by StringDelegate()
}

// Map delegation
class UserFromMap(map: Map<String, Any?>) {
    val name: String by map
    val age: Int by map
    val email: String by map
}

fun mapDelegationDemo() {
    val user = UserFromMap(mapOf(
        "name" to "Alice",
        "age" to 30,
        "email" to "alice@example.com"
    ))
    
    println("${user.name}, ${user.age}, ${user.email}")
}
```

### Generics

```kotlin
// Generic class
class Box<T>(val value: T) {
    fun get(): T = value
    
    override fun toString() = "Box($value)"
}

// Generic function
fun <T> singletonList(item: T): List<T> {
    return listOf(item)
}

// Generic constraints
fun <T : Comparable<T>> max(a: T, b: T): T {
    return if (a > b) a else b
}

fun <T : Number> sum(numbers: List<T>): Double {
    return numbers.sumOf { it.toDouble() }
}

// Multiple constraints
interface HasName {
    val name: String
}

fun <T> printName(item: T) where T : HasName, T : Comparable<T> {
    println(item.name)
}

// Variance
// Covariant (out)
interface Producer<out T> {
    fun produce(): T
}

// Contravariant (in)
interface Consumer<in T> {
    fun consume(item: T)
}

// Star projection
fun printList(list: List<*>) {
    list.forEach { println(it) }
}

// Reified type parameters
inline fun <reified T> isInstance(value: Any): Boolean {
    return value is T
}

fun genericsDemo() {
    val intBox = Box(42)
    val stringBox = Box("Hello")
    
    println(intBox.get())
    println(stringBox.get())
    
    val list = singletonList("Kotlin")
    println(list)
    
    println(max(5, 10))
    println(max("apple", "banana"))
    
    println(isInstance<String>("hello"))
    println(isInstance<Int>("hello"))
}
```

## 7. Functional Programming Concepts

### Lambdas and Higher-Order Functions

```kotlin
fun functionalDemo() {
    val numbers = listOf(1, 2, 3, 4, 5)
    
    // Map
    val doubled = numbers.map { it * 2 }
    val squared = numbers.map { n -> n * n }
    
    // Filter
    val evens = numbers.filter { it % 2 == 0 }
    val greaterThan2 = numbers.filter { it > 2 }
    
    // Reduce and fold
    val sum = numbers.reduce { acc, n -> acc + n }
    val product = numbers.fold(1) { acc, n -> acc * n }
    
    // FlatMap
    val nested = listOf(listOf(1, 2), listOf(3, 4))
    val flattened = nested.flatMap { it }
    
    // Associate
    val numberMap = numbers.associateWith { it * it }
    val stringMap = numbers.associateBy { "num_$it" }
    
    // GroupBy
    val grouped = numbers.groupBy { it % 2 }
    
    // Partition
    val (evens2, odds) = numbers.partition { it % 2 == 0 }
    
    // Find
    val first = numbers.find { it > 3 }
    val last = numbers.findLast { it > 3 }
    
    // Any, all, none
    println(numbers.any { it > 3 })
    println(numbers.all { it > 0 })
    println(numbers.none { it < 0 })
    
    // TakeWhile, dropWhile
    println(numbers.takeWhile { it < 4 })
    println(numbers.dropWhile { it < 3 })
}

// Function composition
infix fun <A, B, C> ((A) -> B).andThen(g: (B) -> C): (A) -> C {
    return { a -> g(this(a)) }
}

infix fun <A, B, C> ((B) -> C).compose(g: (A) -> B): (A) -> C {
    return { a -> this(g(a)) }
}

fun compositionDemo() {
    val double: (Int) -> Int = { it * 2 }
    val addFive: (Int) -> Int = { it + 5 }
    val square: (Int) -> Int = { it * it }
    
    val doubleThenAddFive = double andThen addFive
    val addFiveThenDouble = addFive compose double
    
    println(doubleThenAddFive(3))  // (3 * 2) + 5 = 11
    println(addFiveThenDouble(3))  // (3 + 5) * 2 = 16
}
```

### Immutability

```kotlin
// Immutable data classes
data class Point(val x: Int, val y: Int) {
    fun move(dx: Int, dy: Int) = Point(x + dx, y + dy)
    fun scale(factor: Int) = Point(x * factor, y * factor)
}

// Immutable collections
fun immutabilityDemo() {
    val original = listOf(1, 2, 3)
    
    // Operations return new collections
    val withFour = original + 4
    val withoutTwo = original.filter { it != 2 }
    val doubled = original.map { it * 2 }
    
    println(original)   // [1, 2, 3]
    println(withFour)   // [1, 2, 3, 4]
    println(withoutTwo) // [1, 3]
    println(doubled)    // [2, 4, 6]
    
    // Point example
    val point = Point(3, 4)
    val moved = point.move(2, 1)
    val scaled = point.scale(2)
    
    println(point)   // Point(3, 4)
    println(moved)   // Point(5, 5)
    println(scaled)  // Point(6, 8)
}

// Builder pattern for immutability
fun buildList(builderAction: MutableList<Int>.() -> Unit): List<Int> {
    val list = mutableListOf<Int>()
    list.builderAction()
    return list.toList()
}

fun builderDemo() {
    val list = buildList {
        add(1)
        add(2)
        add(3)
    }
    
    println(list)
}
```

### Functional Patterns

```kotlin
// Currying
fun <A, B, C> curry(f: (A, B) -> C): (A) -> (B) -> C {
    return { a -> { b -> f(a, b) } }
}

fun <A, B, C, D> curry(f: (A, B, C) -> D): (A) -> (B) -> (C) -> D {
    return { a -> { b -> { c -> f(a, b, c) } } }
}

fun curryingDemo() {
    val add = { a: Int, b: Int -> a + b }
    val curriedAdd = curry(add)
    
    val add5 = curriedAdd(5)
    println(add5(3))  // 8
    println(add5(10)) // 15
    
    val greet = { greeting: String, name: String -> "$greeting, $name!" }
    val curriedGreet = curry(greet)
    
    val sayHello = curriedGreet("Hello")
    println(sayHello("Alice"))  // Hello, Alice!
    println(sayHello("Bob"))    // Hello, Bob!
}

// Memoization
fun <A, R> memoize(fn: (A) -> R): (A) -> R {
    val cache = mutableMapOf<A, R>()
    return { a ->
        cache.getOrPut(a) { fn(a) }
    }
}

val fibonacci: (Int) -> Long = memoize { n ->
    when {
        n <= 1 -> n.toLong()
        else -> fibonacci(n - 1) + fibonacci(n - 2)
    }
}

// Tail recursion
tailrec fun factorial(n: Long, accumulator: Long = 1): Long {
    return if (n <= 1) accumulator
    else factorial(n - 1, n * accumulator)
}

tailrec fun gcd(a: Int, b: Int): Int {
    return if (b == 0) a
    else gcd(b, a % b)
}

// Monads (Option/Maybe pattern)
sealed class Option<out T> {
    object None : Option<Nothing>()
    data class Some<T>(val value: T) : Option<T>()
    
    fun <R> map(transform: (T) -> R): Option<R> = when (this) {
        is None -> None
        is Some -> Some(transform(value))
    }
    
    fun <R> flatMap(transform: (T) -> Option<R>): Option<R> = when (this) {
        is None -> None
        is Some -> transform(value)
    }
    
    fun getOrElse(default: () -> T): T = when (this) {
        is None -> default()
        is Some -> value
    }
}

fun optionDemo() {
    val some = Option.Some(42)
    val none = Option.None
    
    val doubled = some.map { it * 2 }
    val doubledNone = none.map { (it as Int) * 2 }
    
    println(doubled)      // Some(84)
    println(doubledNone)  // None
}
```

## 8. Memory Management

### Garbage Collection

```kotlin
// Kotlin uses JVM's garbage collection
// Objects are automatically freed when no longer referenced

class LargeObject(val data: ByteArray) {
    init {
        println("LargeObject created")
    }
}

fun garbageCollectionDemo() {
    // Object created
    var obj: LargeObject? = LargeObject(ByteArray(1000000))
    
    // Use object
    println("Size: ${obj?.data?.size}")
    
    // Remove reference - eligible for GC
    obj = null
    
    // Suggest GC (not guaranteed)
    System.gc()
}

// Avoiding memory leaks
// 1. Close resources
fun useResources() {
    // use() automatically closes
    java.io.File("test.txt").bufferedReader().use { reader ->
        reader.readLines().forEach { println(it) }
    }
}

// 2. Clear collections
class Cache {
    private val items = mutableMapOf<String, Any>()
    
    fun add(key: String, value: Any) {
        items[key] = value
    }
    
    fun clear() {
        items.clear() // Free memory
    }
}

// 3. WeakReference
import java.lang.ref.WeakReference

class ImageCache {
    private val cache = mutableMapOf<String, WeakReference<ByteArray>>()
    
    fun store(key: String, image: ByteArray) {
        cache[key] = WeakReference(image)
    }
    
    fun retrieve(key: String): ByteArray? {
        return cache[key]?.get()
    }
    
    fun cleanup() {
        cache.entries.removeIf { it.value.get() == null }
    }
}
```

### Performance Optimization

```kotlin
// Inline functions (no overhead)
inline fun measureTime(block: () -> Unit): Long {
    val start = System.currentTimeMillis()
    block()
    return System.currentTimeMillis() - start
}

// Use sequences for large collections
fun sequenceOptimization() {
    val list = (1..1_000_000).toList()
    
    // Eager evaluation (creates intermediate lists)
    val result1 = list
        .map { it * 2 }
        .filter { it > 1000 }
        .take(10)
    
    // Lazy evaluation (no intermediate lists)
    val result2 = list.asSequence()
        .map { it * 2 }
        .filter { it > 1000 }
        .take(10)
        .toList()
}

// Use primitive arrays
fun arrayOptimization() {
    // Boxed array (uses objects)
    val boxedArray = arrayOf(1, 2, 3, 4, 5)
    
    // Primitive array (no boxing)
    val primitiveArray = intArrayOf(1, 2, 3, 4, 5)
}

// Use const for compile-time constants
const val MAX_SIZE = 100
const val API_KEY = "key123"

// Object pool pattern
class ObjectPool<T>(
    private val factory: () -> T,
    private val reset: (T) -> Unit
) {
    private val pool = mutableListOf<T>()
    
    fun acquire(): T {
        return if (pool.isNotEmpty()) pool.removeLast()
        else factory()
    }
    
    fun release(obj: T) {
        reset(obj)
        pool.add(obj)
    }
}

// StringBuilder for string building
fun stringBuilding() {
    // Inefficient
    var result = ""
    for (i in 1..1000) {
        result += i.toString()
    }
    
    // Efficient
    val result2 = buildString {
        for (i in 1..1000) {
            append(i)
        }
    }
}
```

## 9. Standard Library

### Collections

```kotlin
import kotlin.collections.*

fun collectionsLibraryDemo() {
    val list = listOf(1, 2, 3, 4, 5)
    
    // Aggregate operations
    println(list.sum())
    println(list.average())
    println(list.minOrNull())
    println(list.maxOrNull())
    println(list.count())
    
    // Transformation
    println(list.map { it * 2 })
    println(list.mapIndexed { index, value -> index to value })
    println(list.mapNotNull { if (it % 2 == 0) it else null })
    
    // Filtering
    println(list.filter { it > 2 })
    println(list.filterIndexed { index, _ -> index % 2 == 0 })
    println(list.filterNot { it % 2 == 0 })
    
    // Grouping
    println(list.groupBy { it % 2 })
    println(list.partition { it % 2 == 0 })
    
    // Sorting
    println(list.sorted())
    println(list.sortedDescending())
    println(list.sortedBy { -it })
    
    // Distinct
    println(listOf(1, 2, 2, 3, 3, 3).distinct())
    
    // Chunking
    println(list.chunked(2))
    println(list.windowed(3))
    
    // Zipping
    val list2 = listOf("a", "b", "c")
    println(list.zip(list2))
}
```

### Ranges and Progressions

```kotlin
fun rangesDemo() {
    // Int ranges
    val range1 = 1..10
    val range2 = 1 until 10
    val range3 = 10 downTo 1
    val range4 = 1..10 step 2
    
    // Char ranges
    val alphabet = 'a'..'z'
    
    // Contains
    println(5 in range1)
    println(15 !in range1)
    
    // Iteration
    for (i in 1..5) {
        println(i)
    }
    
    for (c in 'A'..'E') {
        println(c)
    }
    
    // Progression properties
    println(range1.first)
    println(range1.last)
    println(range1.step)
}
```

### String Operations

```kotlin
fun stringOperationsDemo() {
    val str = "Hello, Kotlin!"
    
    // Properties
    println(str.length)
    println(str.indices)
    println(str.lastIndex)
    
    // Access
    println(str[0])
    println(str.first())
    println(str.last())
    println(str.getOrNull(100))
    
    // Substrings
    println(str.substring(0, 5))
    println(str.substring(7))
    println(str.take(5))
    println(str.takeLast(7))
    println(str.drop(7))
    
    // Case
    println(str.uppercase())
    println(str.lowercase())
    println(str.capitalize())
    
    // Trimming
    println("  hello  ".trim())
    println("  hello  ".trimStart())
    println("  hello  ".trimEnd())
    
    // Replace
    println(str.replace("Kotlin", "World"))
    println(str.replaceFirst("l", "L"))
    
    // Split
    println("a,b,c,d".split(","))
    println("a1b2c3".split(Regex("\\d")))
    
    // Contains
    println(str.contains("Kotlin"))
    println(str.startsWith("Hello"))
    println(str.endsWith("!"))
    
    // Padding
    println("42".padStart(5, '0'))
    println("42".padEnd(5, '0'))
    
    // Repeat
    println("Hello ".repeat(3))
    
    // Lines
    val multiLine = """
        Line 1
        Line 2
        Line 3
    """.trimIndent()
    println(multiLine.lines())
}
```

### Regex

```kotlin
fun regexDemo() {
    val pattern = Regex("\\d+")
    val text = "There are 123 apples and 456 oranges"
    
    // Find
    val match = pattern.find(text)
    println(match?.value)
    println(match?.range)
    
    // Find all
    val matches = pattern.findAll(text)
    matches.forEach { println(it.value) }
    
    // Matches
    println(Regex("\\d+").matches("123"))
    println(Regex("\\d+").matches("abc"))
    
    // Contains
    println(text.contains(pattern))
    
    // Replace
    println(pattern.replace(text, "X"))
    
    // Split
    println("a1b2c3".split(Regex("\\d")))
    
    // Groups
    val datePattern = Regex("""(\d{4})-(\d{2})-(\d{2})""")
    val dateMatch = datePattern.find("2024-01-15")
    val (year, month, day) = dateMatch!!.destructured
    println("Year: $year, Month: $month, Day: $day")
}
```

### File I/O

```kotlin
import java.io.File

fun fileIODemo() {
    val file = File("test.txt")
    
    // Write
    file.writeText("Hello, Kotlin!")
    file.appendText("\nNew line")
    
    // Read
    val content = file.readText()
    val lines = file.readLines()
    
    // Read with use
    file.bufferedReader().use { reader ->
        reader.lineSequence().forEach { line ->
            println(line)
        }
    }
    
    // Write lines
    file.writeText("")
    file.appendText("Line 1\n")
    file.appendText("Line 2\n")
    
    // Properties
    println(file.name)
    println(file.path)
    println(file.absolutePath)
    println(file.exists())
    println(file.isFile)
    println(file.isDirectory)
    println(file.length())
    
    // Directory operations
    val dir = File("mydir")
    dir.mkdir()
    dir.mkdirs()
    
    dir.listFiles()?.forEach { println(it.name) }
    
    // Delete
    file.delete()
    dir.deleteRecursively()
    
    // Walking directory tree
    File(".").walk()
        .filter { it.isFile }
        .filter { it.extension == "kt" }
        .forEach { println(it.path) }
}
```

## 10. Tooling and Ecosystem

### Gradle Build

```kotlin
// build.gradle.kts
plugins {
    kotlin("jvm") version "1.9.0"
}

group = "com.example"
version = "1.0-SNAPSHOT"

repositories {
    mavenCentral()
}

dependencies {
    implementation(kotlin("stdlib"))
    testImplementation(kotlin("test"))
}

tasks.test {
    useJUnitPlatform()
}
```

### Testing

```kotlin
import org.junit.jupiter.api.Test
import org.junit.jupiter.api.Assertions.*

class CalculatorTest {
    @Test
    fun `add returns sum of two numbers`() {
        val calculator = Calculator()
        assertEquals(8, calculator.add(5, 3))
    }
    
    @Test
    fun `divide by zero throws exception`() {
        val calculator = Calculator()
        assertThrows<ArithmeticException> {
            calculator.divide(10, 0)
        }
    }
}

class Calculator {
    fun add(a: Int, b: Int) = a + b
    fun subtract(a: Int, b: Int) = a - b
    fun multiply(a: Int, b: Int) = a * b
    fun divide(a: Int, b: Int): Int {
        if (b == 0) throw ArithmeticException("Division by zero")
        return a / b
    }
}

// Kotest (alternative testing framework)
import io.kotest.core.spec.style.StringSpec
import io.kotest.matchers.shouldBe

class CalculatorSpec : StringSpec({
    "add should return sum" {
        Calculator().add(5, 3) shouldBe 8
    }
    
    "subtract should return difference" {
        Calculator().subtract(5, 3) shouldBe 2
    }
})
```

### Coroutines

```kotlin
import kotlinx.coroutines.*

fun coroutinesExample() = runBlocking {
    // Launch coroutine
    launch {
        delay(1000)
        println("World!")
    }
    println("Hello,")
    
    // Async/await
    val deferred = async {
        delay(1000)
        "Result"
    }
    println(deferred.await())
    
    // Parallel execution
    val time = measureTimeMillis {
        val one = async { doSomethingUsefulOne() }
        val two = async { doSomethingUsefulTwo() }
        println("The answer is ${one.await() + two.await()}")
    }
    println("Completed in $time ms")
}

suspend fun doSomethingUsefulOne(): Int {
    delay(1000)
    return 13
}

suspend fun doSomethingUsefulTwo(): Int {
    delay(1000)
    return 29
}
```

## 11. Best Practices

### Code Style

```kotlin
// Use val over var
val immutable = "value"
var mutable = 0

// Use expression bodies for simple functions
fun double(x: Int) = x * 2

// Use when instead of if-else chains
fun describe(obj: Any) = when (obj) {
    is String -> "String: $obj"
    is Int -> "Int: $obj"
    else -> "Unknown"
}

// Use data classes
data class User(val id: Int, val name: String)

// Use named arguments
createUser(
    id = 1,
    name = "Alice",
    email = "alice@example.com"
)

// Use scope functions
val result = "Hello".let { str ->
    str.uppercase()
}

person.apply {
    name = "Alice"
    age = 30
}

// Use extension functions
fun String.isPalindrome() = this == this.reversed()

// Use sealed classes for restricted hierarchies
sealed class Result {
    data class Success(val data: String) : Result()
    data class Error(val message: String) : Result()
}
```

### Null Safety

```kotlin
// Prefer non-nullable types
fun getName(): String = "Alice"

// Use safe call operator
val length = nullableString?.length

// Use Elvis operator
val displayName = userName ?: "Guest"

// Use let for null checks
nullableValue?.let { value ->
    // Use value here
}

// Avoid !!
// BAD:
val length = nullableString!!.length

// GOOD:
val length = nullableString?.length ?: 0
```

### Performance

```kotlin
// Use inline functions
inline fun <T> lock(lock: Lock, body: () -> T): T {
    lock.lock()
    try {
        return body()
    } finally {
        lock.unlock()
    }
}

// Use sequences for large collections
(1..1_000_000).asSequence()
    .map { it * 2 }
    .filter { it > 1000 }
    .take(10)
    .toList()

// Use primitive arrays
val intArray = intArrayOf(1, 2, 3)

// Use const for constants
const val MAX_COUNT = 100

// Avoid creating objects in loops
// BAD:
for (i in 1..1000) {
    val temp = StringBuilder()
    temp.append(i)
}

// GOOD:
val sb = StringBuilder()
for (i in 1..1000) {
    sb.append(i)
}
```

## 12. Conclusion

### Key Takeaways

Kotlin is a modern, powerful programming language that offers:

1. **Conciseness**: Less boilerplate, more readable code
2. **Safety**: Null safety and type system prevent common errors
3. **Interoperability**: Seamless Java integration
4. **Versatility**: JVM, Android, JavaScript, Native
5. **Modern Features**: Coroutines, extension functions, data classes
6. **Tooling**: Excellent IDE support and build tools
7. **Community**: Growing ecosystem and community support

### Learning Path

1. **Basics**: Master syntax, types, and control flow
2. **OOP**: Learn classes, inheritance, and interfaces
3. **Functions**: Higher-order functions and lambdas
4. **Collections**: Standard library collections
5. **Coroutines**: Async programming
6. **Android**: Android app development
7. **Multiplatform**: Kotlin Multiplatform Mobile
8. **Backend**: Spring Boot or Ktor

### Resources

- **Official Docs**: kotlinlang.org
- **Kotlin Playground**: play.kotlinlang.org
- **Android**: developer.android.com/kotlin
- **Spring**: spring.io/guides/tutorials/spring-boot-kotlin
- **Ktor**: ktor.io

### Next Steps

1. Build Android apps
2. Explore Kotlin Multiplatform
3. Learn coroutines and Flow
4. Build backend services with Ktor or Spring Boot
5. Contribute to open source
6. Study design patterns in Kotlin
7. Join the Kotlin community

This guide covers the essential aspects of Kotlin programming. Continue practicing and building projects to master the language!
