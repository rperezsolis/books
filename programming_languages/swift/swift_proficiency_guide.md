# Swift Programming Language Proficiency Guide

## 1. Introduction

Swift is a powerful and intuitive programming language developed by Apple for iOS, macOS, watchOS, and tvOS app development. Introduced in 2014, Swift combines the best of modern language thinking with wisdom from Apple's engineering culture, creating a fast, safe, and expressive language.

### Key Characteristics

- **Safe**: Eliminates entire classes of unsafe code
- **Fast**: Built for performance from the ground up
- **Expressive**: Clean, modern syntax that's enjoyable to use
- **Open source**: Available on multiple platforms
- **Type-safe**: Strong typing with type inference
- **Memory-safe**: Automatic memory management

### Why Learn Swift?

- **iOS/macOS development**: Primary language for Apple platforms
- **Modern features**: Optionals, generics, closures, protocols
- **Performance**: As fast as C-based languages
- **Safety**: Reduces bugs and crashes
- **Growing ecosystem**: SwiftUI, Combine, async/await
- **Career opportunities**: High demand for iOS developers

### Setting Up Swift

```bash
# macOS: Xcode includes Swift
# Download from Mac App Store

# Linux: Install Swift
curl https://swift.org/install/linux
tar xzf swift-<version>.tar.gz
export PATH=/path/to/swift/usr/bin:$PATH

# Verify installation
swift --version

# Swift REPL
swift

# Compile and run
swiftc hello.swift
./hello
```

### Hello World

```swift
// hello.swift
print("Hello, Swift!")

// Run with:
// swift hello.swift
// or compile:
// swiftc hello.swift && ./hello
```

## 2. Core Language Mechanics

### Syntax Fundamentals

```swift
// Comments
// Single-line comment
/* Multi-line
   comment */

// Documentation comments
/// This is a documentation comment
/// - Parameter name: The name parameter
/// - Returns: A greeting string

// Statements don't require semicolons
let x = 5
print(x)

// But semicolons are allowed
let y = 10; print(y)

// Code blocks use curly braces
if true {
    print("Block statement")
}

// Imports
import Foundation
import UIKit
```

### Variables and Constants

```swift
func variablesDemo() {
    // let - immutable constant
    let name = "Alice"
    let age = 30
    // name = "Bob" // ERROR: Cannot assign to value
    
    // var - mutable variable
    var count = 0
    count = 1 // OK
    
    // Explicit types
    let city: String = "New York"
    let population: Int = 8000000
    let temperature: Double = 72.5
    let isCapital: Bool = false
    
    // Type inference
    let inferred = "Hello"  // Type: String
    let number = 42         // Type: Int
    
    // Multiple declarations
    let (x, y) = (10, 20)
    var a = 1, b = 2, c = 3
    
    // Lazy initialization
    lazy var expensiveResource: String = {
        print("Computing...")
        return "Computed value"
    }()
    
    // Static properties
    struct Config {
        static let apiKey = "key123"
        static let maxConnections = 100
    }
}
```

### Data Types

```swift
func dataTypesDemo() {
    // Integers
    let int8: Int8 = 127
    let int16: Int16 = 32767
    let int32: Int32 = 2_147_483_647
    let int64: Int64 = 9_223_372_036_854_775_807
    let int: Int = 42 // Platform-dependent (32 or 64-bit)
    
    let uint: UInt = 42
    let uint8: UInt8 = 255
    
    // Floating-point
    let float: Float = 3.14
    let double: Double = 3.14159
    
    // Type conversions
    let integer = 42
    let double = Double(integer)
    let string = String(integer)
    
    // Numeric literals
    let decimal = 42
    let binary = 0b101010
    let octal = 0o52
    let hex = 0x2A
    
    // Underscores in numbers
    let million = 1_000_000
    let creditCard = 1234_5678_9012_3456
    
    // Booleans
    let isTrue: Bool = true
    let isFalse: Bool = false
    
    // Strings
    let singleLine = "Hello, Swift!"
    let multiLine = """
        Line 1
        Line 2
        Line 3
        """
    
    // String interpolation
    let name = "Alice"
    let age = 30
    print("\(name) is \(age) years old")
    print("Next year: \(age + 1)")
    
    // String methods
    let text = "Hello"
    print(text.count)
    print(text.uppercased())
    print(text.lowercased())
    print(text.hasPrefix("He"))
    print(text.hasSuffix("lo"))
    print(text.contains("ell"))
    
    // Characters
    let char: Character = "A"
    for character in "Hello" {
        print(character)
    }
    
    // Tuples
    let point = (10, 20)
    let person = (name: "Alice", age: 30)
    
    // Access tuple elements
    print(point.0, point.1)
    print(person.name, person.age)
    
    // Tuple decomposition
    let (x, y) = point
    let (userName, userAge) = person
    
    // Ignore values
    let (_, age2) = person
    
    // Type aliases
    typealias Point = (x: Int, y: Int)
    typealias UserID = Int
}
```

### Optionals and Null Safety

```swift
func optionalsDemo() {
    // Optional types
    var name: String? = "Alice"
    name = nil // OK
    
    var age: Int? = 30
    age = nil
    
    // Forced unwrapping (use with caution)
    let definitelyHasValue: String? = "Hello"
    let unwrapped = definitelyHasValue!
    
    // Optional binding (if let)
    if let userName = name {
        print("Name is \(userName)")
    } else {
        print("Name is nil")
    }
    
    // Optional binding with multiple values
    if let name = name, let age = age {
        print("\(name) is \(age) years old")
    }
    
    // Guard statement
    func greet(name: String?) {
        guard let userName = name else {
            print("No name provided")
            return
        }
        print("Hello, \(userName)!")
    }
    
    // Nil coalescing operator
    let displayName = name ?? "Guest"
    let userAge = age ?? 0
    
    // Optional chaining
    struct Person {
        var address: Address?
    }
    
    struct Address {
        var street: String
        var city: String
    }
    
    let person: Person? = Person(address: Address(street: "Main St", city: "NYC"))
    let city = person?.address?.city
    
    // Implicitly unwrapped optionals
    var assumedString: String! = "Hello"
    let implicitString: String = assumedString // No need to unwrap
    
    // Optional map and flatMap
    let number: Int? = 42
    let doubled = number.map { $0 * 2 }
    
    let nested: Int?? = 42
    let flattened = nested.flatMap { $0 }
}
```

### Operators

```swift
func operatorsDemo() {
    // Arithmetic
    print(5 + 3)    // 8
    print(5 - 3)    // 2
    print(5 * 3)    // 15
    print(5 / 3)    // 1 (integer division)
    print(5.0 / 3.0) // 1.666...
    print(5 % 3)    // 2
    
    // Compound assignment
    var x = 10
    x += 5  // x = x + 5
    x -= 3  // x = x - 3
    x *= 2  // x = x * 2
    x /= 4  // x = x / 4
    
    // Comparison
    print(5 == 3)   // false
    print(5 != 3)   // true
    print(5 > 3)    // true
    print(5 < 3)    // false
    print(5 >= 3)   // true
    print(5 <= 3)   // false
    
    // Logical
    print(true && false)  // false
    print(true || false)  // true
    print(!true)          // false
    
    // Range operators
    let closedRange = 1...5      // 1, 2, 3, 4, 5
    let halfOpenRange = 1..<5    // 1, 2, 3, 4
    let oneSidedRange = 2...     // 2 to infinity
    let upToRange = ..<5         // up to 5
    
    // Ternary conditional
    let age = 20
    let status = age >= 18 ? "Adult" : "Minor"
    
    // Nil-coalescing
    let name: String? = nil
    let displayName = name ?? "Guest"
    
    // Identity operators
    class Person { let name: String; init(name: String) { self.name = name } }
    let person1 = Person(name: "Alice")
    let person2 = Person(name: "Alice")
    let person3 = person1
    
    print(person1 === person3)  // true (same instance)
    print(person1 === person2)  // false (different instances)
    print(person1 !== person2)  // true
    
    // Bitwise operators
    let bits1: UInt8 = 0b1010
    let bits2: UInt8 = 0b1100
    
    print(bits1 & bits2)   // 0b1000 (AND)
    print(bits1 | bits2)   // 0b1110 (OR)
    print(bits1 ^ bits2)   // 0b0110 (XOR)
    print(~bits1)          // 0b11110101 (NOT)
    print(bits1 << 1)      // 0b10100 (left shift)
    print(bits1 >> 1)      // 0b101 (right shift)
}
```

### Type System

```swift
func typeSystemDemo() {
    // Type inference
    let str = "Hello"      // String
    let num = 42           // Int
    let dec = 3.14         // Double
    
    // Explicit types
    let name: String = "Alice"
    let age: Int = 30
    
    // Any and AnyObject
    var any: Any = "Can be anything"
    any = 42
    any = true
    
    var anyObject: AnyObject = NSString(string: "Object")
    
    // Type casting
    let value: Any = 42
    
    if value is Int {
        print("It's an Int")
    }
    
    if let intValue = value as? Int {
        print("Casted to Int: \(intValue)")
    }
    
    let definitelyInt = value as! Int // Force cast
    
    // Type checking and casting patterns
    func describe(_ value: Any) {
        switch value {
        case is String:
            print("It's a string")
        case let int as Int:
            print("It's an Int: \(int)")
        case let (x, y) as (Int, Int):
            print("It's a point: \(x), \(y)")
        default:
            print("Unknown type")
        }
    }
    
    // Generic functions
    func swapValues<T>(_ a: inout T, _ b: inout T) {
        let temp = a
        a = b
        b = temp
    }
    
    var x = 5, y = 10
    swapValues(&x, &y)
    
    // Associated types
    protocol Container {
        associatedtype Item
        mutating func append(_ item: Item)
        var count: Int { get }
        subscript(i: Int) -> Item { get }
    }
}
```

## 3. Control Flow

### Conditional Statements

```swift
func conditionalsDemo() {
    let age = 20
    
    // if-else
    if age < 18 {
        print("Minor")
    } else if age < 65 {
        print("Adult")
    } else {
        print("Senior")
    }
    
    // Ternary operator
    let status = age >= 18 ? "Adult" : "Minor"
    
    // if with optional binding
    let name: String? = "Alice"
    if let userName = name {
        print("Name is \(userName)")
    }
    
    // Guard statement
    func processUser(name: String?) {
        guard let userName = name else {
            print("No name provided")
            return
        }
        print("Processing \(userName)")
    }
    
    // Switch statement
    let grade = "B"
    switch grade {
    case "A":
        print("Excellent")
    case "B":
        print("Good")
    case "C":
        print("Average")
    case "D", "F":
        print("Poor")
    default:
        print("Invalid grade")
    }
    
    // Switch with ranges
    let score = 85
    switch score {
    case 90...100:
        print("A")
    case 80..<90:
        print("B")
    case 70..<80:
        print("C")
    case 60..<70:
        print("D")
    default:
        print("F")
    }
    
    // Switch with tuples
    let point = (1, 1)
    switch point {
    case (0, 0):
        print("Origin")
    case (_, 0):
        print("On X-axis")
    case (0, _):
        print("On Y-axis")
    case (-2...2, -2...2):
        print("Inside box")
    default:
        print("Outside box")
    }
    
    // Switch with value binding
    let anotherPoint = (2, 0)
    switch anotherPoint {
    case (let x, 0):
        print("On X-axis at \(x)")
    case (0, let y):
        print("On Y-axis at \(y)")
    case let (x, y):
        print("At (\(x), \(y))")
    }
    
    // Switch with where clause
    let yetAnotherPoint = (1, -1)
    switch yetAnotherPoint {
    case let (x, y) where x == y:
        print("On diagonal")
    case let (x, y) where x == -y:
        print("On anti-diagonal")
    case let (x, y):
        print("At (\(x), \(y))")
    }
    
    // Switch with enums
    enum Direction {
        case north, south, east, west
    }
    
    let direction = Direction.north
    switch direction {
    case .north:
        print("Going north")
    case .south:
        print("Going south")
    case .east:
        print("Going east")
    case .west:
        print("Going west")
    }
}
```

### Loops

```swift
func loopsDemo() {
    // For-in with range
    for i in 1...5 {
        print(i)
    }
    
    for i in 1..<5 {
        print(i) // 1, 2, 3, 4
    }
    
    // For-in with stride
    for i in stride(from: 0, to: 10, by: 2) {
        print(i) // 0, 2, 4, 6, 8
    }
    
    for i in stride(from: 10, through: 0, by: -2) {
        print(i) // 10, 8, 6, 4, 2, 0
    }
    
    // For-in with collections
    let fruits = ["apple", "banana", "orange"]
    for fruit in fruits {
        print(fruit)
    }
    
    // For-in with enumerated
    for (index, fruit) in fruits.enumerated() {
        print("\(index): \(fruit)")
    }
    
    // For-in with dictionary
    let ages = ["Alice": 30, "Bob": 25]
    for (name, age) in ages {
        print("\(name) is \(age) years old")
    }
    
    // While loop
    var count = 0
    while count < 5 {
        print(count)
        count += 1
    }
    
    // Repeat-while loop
    var num = 0
    repeat {
        print(num)
        num += 1
    } while num < 5
    
    // Break and continue
    for i in 1...10 {
        if i == 3 { continue }
        if i == 7 { break }
        print(i)
    }
    
    // Labeled statements
    outerLoop: for i in 1...3 {
        for j in 1...3 {
            if i == 2 && j == 2 {
                break outerLoop
            }
            print("(\(i), \(j))")
        }
    }
    
    // Where clause in for-in
    let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    for number in numbers where number % 2 == 0 {
        print(number) // Only even numbers
    }
}
```

### Error Handling

```swift
// Define errors
enum ValidationError: Error {
    case invalidAge
    case invalidEmail
    case missingField(String)
}

enum NetworkError: Error {
    case noConnection
    case timeout
    case serverError(Int)
}

func errorHandlingDemo() {
    // Throwing function
    func validateAge(_ age: Int) throws {
        if age < 0 {
            throw ValidationError.invalidAge
        }
    }
    
    // Do-catch
    do {
        try validateAge(-5)
    } catch ValidationError.invalidAge {
        print("Age cannot be negative")
    } catch {
        print("Unknown error: \(error)")
    }
    
    // Multiple catch blocks
    func processData() throws {
        throw NetworkError.serverError(500)
    }
    
    do {
        try processData()
    } catch NetworkError.noConnection {
        print("No connection")
    } catch NetworkError.timeout {
        print("Request timed out")
    } catch NetworkError.serverError(let code) {
        print("Server error: \(code)")
    } catch {
        print("Other error: \(error)")
    }
    
    // Try? (convert to optional)
    let result = try? validateAge(30) // nil if throws
    
    // Try! (force try - crashes if throws)
    let definiteResult = try! validateAge(30)
    
    // Rethrowing functions
    func performOperation(_ operation: () throws -> Void) rethrows {
        try operation()
    }
    
    // Defer (cleanup code)
    func processFile() throws {
        let file = openFile()
        defer {
            file.close() // Runs when scope exits
        }
        
        try file.read()
        try file.write()
        // file.close() runs here
    }
    
    // Result type
    func divide(_ a: Int, _ b: Int) -> Result<Int, NetworkError> {
        if b == 0 {
            return .failure(.serverError(400))
        }
        return .success(a / b)
    }
    
    let divisionResult = divide(10, 2)
    switch divisionResult {
    case .success(let value):
        print("Result: \(value)")
    case .failure(let error):
        print("Error: \(error)")
    }
}
```

## 4. Functions and Code Organization

### Function Basics

```swift
// Basic function
func greet(name: String) {
    print("Hello, \(name)!")
}

// Function with return value
func add(a: Int, b: Int) -> Int {
    return a + b
}

// Implicit return (single expression)
func multiply(a: Int, b: Int) -> Int {
    a * b
}

// Multiple return values (tuple)
func getMinMax(array: [Int]) -> (min: Int, max: Int) {
    return (array.min()!, array.max()!)
}

let bounds = getMinMax(array: [1, 2, 3, 4, 5])
print("Min: \(bounds.min), Max: \(bounds.max)")

// Optional return
func findUser(id: Int) -> String? {
    if id > 0 {
        return "User \(id)"
    }
    return nil
}

// Argument labels
func greet(person name: String, from hometown: String) {
    print("Hello \(name) from \(hometown)!")
}

greet(person: "Alice", from: "NYC")

// Omitting argument labels
func add(_ a: Int, _ b: Int) -> Int {
    a + b
}

add(5, 3)

// Default parameters
func power(base: Int, exponent: Int = 2) -> Int {
    Int(pow(Double(base), Double(exponent)))
}

print(power(base: 2))      // 4
print(power(base: 2, exponent: 3)) // 8

// Variadic parameters
func sum(_ numbers: Int...) -> Int {
    numbers.reduce(0, +)
}

print(sum(1, 2, 3, 4, 5))

// Inout parameters
func swapValues(_ a: inout Int, _ b: inout Int) {
    let temp = a
    a = b
    b = temp
}

var x = 5, y = 10
swapValues(&x, &y)

// Function types
let mathOperation: (Int, Int) -> Int = add
print(mathOperation(5, 3))

// Functions as parameters
func performOperation(_ a: Int, _ b: Int, operation: (Int, Int) -> Int) -> Int {
    operation(a, b)
}

let result = performOperation(5, 3, operation: add)

// Functions as return values
func makeIncrementer(amount: Int) -> (Int) -> Int {
    func incrementer(number: Int) -> Int {
        number + amount
    }
    return incrementer
}

let incrementByTwo = makeIncrementer(amount: 2)
print(incrementByTwo(5)) // 7
```

### Closures

```swift
func closuresDemo() {
    // Basic closure
    let greeting = { (name: String) -> String in
        return "Hello, \(name)!"
    }
    
    print(greeting("Alice"))
    
    // Closure with type inference
    let numbers = [1, 2, 3, 4, 5]
    let doubled = numbers.map { $0 * 2 }
    
    // Trailing closure syntax
    let evens = numbers.filter { $0 % 2 == 0 }
    
    // Multiple trailing closures (Swift 5.3+)
    func fetch(
        onSuccess: (String) -> Void,
        onFailure: (Error) -> Void
    ) {
        // Implementation
    }
    
    fetch {
        print("Success: \($0)")
    } onFailure: {
        print("Failure: \($0)")
    }
    
    // Capturing values
    func makeCounter() -> () -> Int {
        var count = 0
        return {
            count += 1
            return count
        }
    }
    
    let counter = makeCounter()
    print(counter()) // 1
    print(counter()) // 2
    
    // Escaping closures
    var completionHandlers: [() -> Void] = []
    
    func addCompletionHandler(handler: @escaping () -> Void) {
        completionHandlers.append(handler)
    }
    
    // Autoclosure
    func logIfTrue(_ condition: @autoclosure () -> Bool) {
        if condition() {
            print("Condition is true")
        }
    }
    
    logIfTrue(2 + 2 == 4)
}
```

### Methods and Properties

```swift
struct Rectangle {
    var width: Double
    var height: Double
    
    // Computed property
    var area: Double {
        width * height
    }
    
    var perimeter: Double {
        get {
            2 * (width + height)
        }
    }
    
    // Property with setter
    var center: (x: Double, y: Double) {
        get {
            (width / 2, height / 2)
        }
        set {
            width = newValue.x * 2
            height = newValue.y * 2
        }
    }
    
    // Property observers
    var scale: Double = 1.0 {
        willSet {
            print("Will set scale to \(newValue)")
        }
        didSet {
            print("Did set scale from \(oldValue) to \(scale)")
        }
    }
    
    // Instance method
    func describe() {
        print("Rectangle: \(width) x \(height)")
    }
    
    // Mutating method
    mutating func resize(by factor: Double) {
        width *= factor
        height *= factor
    }
    
    // Type method
    static func square(side: Double) -> Rectangle {
        Rectangle(width: side, height: side)
    }
    
    // Subscript
    subscript(index: Int) -> Double {
        get {
            index == 0 ? width : height
        }
        set {
            if index == 0 {
                width = newValue
            } else {
                height = newValue
            }
        }
    }
}

// Lazy properties
class DataManager {
    lazy var data: [String] = {
        print("Loading data...")
        return ["item1", "item2", "item3"]
    }()
}

// Static properties
struct Config {
    static let apiKey = "key123"
    static var maxRetries = 3
}
```

### Async/Await

```swift
// Async functions (Swift 5.5+)
func fetchUser(id: Int) async throws -> String {
    // Simulate network delay
    try await Task.sleep(nanoseconds: 1_000_000_000)
    return "User \(id)"
}

func fetchPosts(userId: Int) async throws -> [String] {
    try await Task.sleep(nanoseconds: 500_000_000)
    return ["Post 1", "Post 2", "Post 3"]
}

func asyncDemo() async {
    // Sequential execution
    do {
        let user = try await fetchUser(id: 1)
        print(user)
        
        let posts = try await fetchPosts(userId: 1)
        print(posts)
    } catch {
        print("Error: \(error)")
    }
    
    // Parallel execution
    async let user = fetchUser(id: 1)
    async let posts = fetchPosts(userId: 1)
    
    do {
        let results = try await (user, posts)
        print(results)
    } catch {
        print("Error: \(error)")
    }
    
    // Task group
    await withTaskGroup(of: String.self) { group in
        for i in 1...3 {
            group.addTask {
                try! await fetchUser(id: i)
            }
        }
        
        for await result in group {
            print(result)
        }
    }
}

// Async sequences
func numberStream() -> AsyncStream<Int> {
    AsyncStream { continuation in
        for i in 1...5 {
            continuation.yield(i)
            Thread.sleep(forTimeInterval: 0.1)
        }
        continuation.finish()
    }
}

func asyncSequenceDemo() async {
    for await number in numberStream() {
        print(number)
    }
}
```

## 5. Data Structures

### Arrays

```swift
func arraysDemo() {
    // Creating arrays
    var numbers = [1, 2, 3, 4, 5]
    let strings: [String] = ["a", "b", "c"]
    var empty: [Int] = []
    var filled = Array(repeating: 0, count: 5)
    
    // Array literal with type inference
    let mixed: [Any] = [1, "two", 3.0]
    
    // Access
    print(numbers[0])       // First element
    print(numbers.first)    // Optional first
    print(numbers.last)     // Optional last
    
    // Modify
    numbers[0] = 10
    numbers[1...3] = [20, 30, 40]
    
    // Add elements
    numbers.append(6)
    numbers.insert(0, at: 0)
    numbers += [7, 8, 9]
    numbers.append(contentsOf: [10, 11])
    
    // Remove elements
    numbers.remove(at: 0)
    numbers.removeLast()
    numbers.removeFirst()
    numbers.removeAll()
    
    // Properties
    print(numbers.count)
    print(numbers.isEmpty)
    print(numbers.capacity)
    
    // Searching
    numbers = [1, 2, 3, 4, 5, 3]
    print(numbers.contains(3))
    print(numbers.firstIndex(of: 3))
    print(numbers.lastIndex(of: 3))
    
    // Sorting
    let unsorted = [3, 1, 4, 1, 5, 9, 2, 6]
    let sorted = unsorted.sorted()
    let sortedDesc = unsorted.sorted(by: >)
    
    var mutable = unsorted
    mutable.sort()
    
    // Filter, map, reduce
    let evens = numbers.filter { $0 % 2 == 0 }
    let doubled = numbers.map { $0 * 2 }
    let sum = numbers.reduce(0, +)
    let product = numbers.reduce(1, *)
    
    // CompactMap (filter nil)
    let optionals: [Int?] = [1, 2, nil, 4, nil]
    let values = optionals.compactMap { $0 }
    
    // FlatMap
    let nested = [[1, 2], [3, 4], [5]]
    let flattened = nested.flatMap { $0 }
    
    // Iteration
    for number in numbers {
        print(number)
    }
    
    for (index, number) in numbers.enumerated() {
        print("\(index): \(number)")
    }
    
    numbers.forEach { print($0) }
    
    // Slicing
    let slice = numbers[1...3]
    let prefix = numbers.prefix(3)
    let suffix = numbers.suffix(3)
    
    // Array transformations
    let reversed = numbers.reversed()
    let shuffled = numbers.shuffled()
    
    // Zip
    let names = ["Alice", "Bob", "Charlie"]
    let ages = [30, 25, 35]
    let zipped = Array(zip(names, ages))
}
```

### Sets

```swift
func setsDemo() {
    // Creating sets
    var numbers: Set<Int> = [1, 2, 3, 4, 5]
    let strings: Set = ["a", "b", "c"]
    var empty: Set<Int> = []
    
    // Add and remove
    numbers.insert(6)
    numbers.remove(1)
    numbers.removeAll()
    
    // Properties
    numbers = [1, 2, 3, 4, 5]
    print(numbers.count)
    print(numbers.isEmpty)
    print(numbers.contains(3))
    
    // Set operations
    let a: Set = [1, 2, 3, 4]
    let b: Set = [3, 4, 5, 6]
    
    // Union
    print(a.union(b))           // {1, 2, 3, 4, 5, 6}
    
    // Intersection
    print(a.intersection(b))    // {3, 4}
    
    // Difference
    print(a.subtracting(b))     // {1, 2}
    
    // Symmetric difference
    print(a.symmetricDifference(b)) // {1, 2, 5, 6}
    
    // Subset and superset
    let c: Set = [1, 2]
    print(c.isSubset(of: a))        // true
    print(a.isSuperset(of: c))      // true
    print(c.isStrictSubset(of: a))  // true
    
    // Disjoint
    let d: Set = [7, 8]
    print(a.isDisjoint(with: d))    // true
    
    // Remove duplicates from array
    let arrayWithDuplicates = [1, 2, 2, 3, 3, 3]
    let unique = Array(Set(arrayWithDuplicates))
    
    // Iteration
    for number in numbers {
        print(number)
    }
}
```

### Dictionaries

```swift
func dictionariesDemo() {
    // Creating dictionaries
    var ages = ["Alice": 30, "Bob": 25, "Charlie": 35]
    let scores: [String: Int] = ["A": 90, "B": 80]
    var empty: [String: Int] = [:]
    
    // Access
    print(ages["Alice"])        // Optional(30)
    print(ages["Alice"]!)       // 30 (force unwrap)
    print(ages["Alice", default: 0]) // 30
    
    // Modify
    ages["Alice"] = 31
    ages["David"] = 40
    ages.updateValue(32, forKey: "Alice")
    
    // Remove
    ages["Bob"] = nil
    ages.removeValue(forKey: "Charlie")
    
    // Properties
    print(ages.count)
    print(ages.isEmpty)
    print(ages.keys)
    print(ages.values)
    
    // Iteration
    for (name, age) in ages {
        print("\(name): \(age)")
    }
    
    for name in ages.keys {
        print(name)
    }
    
    for age in ages.values {
        print(age)
    }
    
    // Dictionary methods
    let keys = ages.keys.sorted()
    let values = Array(ages.values)
    
    // Merge dictionaries
    let defaults = ["theme": "light", "fontSize": 14]
    let userSettings = ["theme": "dark"]
    let merged = defaults.merging(userSettings) { _, new in new }
    
    // Map values
    let doubled = ages.mapValues { $0 * 2 }
    
    // Filter
    let adults = ages.filter { $0.value >= 18 }
    
    // Group by
    let words = ["apple", "banana", "apricot", "berry"]
    let grouped = Dictionary(grouping: words) { $0.first! }
}
```

### Tuples

```swift
func tuplesDemo() {
    // Basic tuples
    let point = (10, 20)
    let person = (name: "Alice", age: 30, city: "NYC")
    
    // Access elements
    print(point.0, point.1)
    print(person.name, person.age, person.city)
    
    // Decomposition
    let (x, y) = point
    let (name, age, city) = person
    
    // Ignore values
    let (userName, _, _) = person
    
    // Return tuple from function
    func getCoordinates() -> (x: Int, y: Int) {
        return (10, 20)
    }
    
    let coordinates = getCoordinates()
    print(coordinates.x, coordinates.y)
    
    // Tuple comparison
    print((1, "a") < (2, "b"))    // true
    print((1, "a") == (1, "a"))   // true
    
    // Tuples in switch
    let point2 = (1, 1)
    switch point2 {
    case (0, 0):
        print("Origin")
    case (_, 0):
        print("On X-axis")
    case (0, _):
        print("On Y-axis")
    default:
        print("Other")
    }
}
```

### Collections Algorithms

```swift
func collectionsAlgorithmsDemo() {
    let numbers = [1, 2, 3, 4, 5]
    
    // Map
    let squared = numbers.map { $0 * $0 }
    let strings = numbers.map(String.init)
    
    // CompactMap
    let optionals: [Int?] = [1, nil, 3, nil, 5]
    let values = optionals.compactMap { $0 }
    
    // FlatMap
    let nested = [[1, 2], [3, 4]]
    let flattened = nested.flatMap { $0 }
    
    // Filter
    let evens = numbers.filter { $0 % 2 == 0 }
    
    // Reduce
    let sum = numbers.reduce(0, +)
    let product = numbers.reduce(1, *)
    
    // First, last
    print(numbers.first)
    print(numbers.last)
    print(numbers.first(where: { $0 > 3 }))
    print(numbers.last(where: { $0 < 3 }))
    
    // Contains
    print(numbers.contains(3))
    print(numbers.contains(where: { $0 > 3 }))
    
    // All, none
    print(numbers.allSatisfy { $0 > 0 })
    
    // Min, max
    print(numbers.min())
    print(numbers.max())
    
    // Sorted
    print(numbers.sorted())
    print(numbers.sorted(by: >))
    
    // Prefix, suffix
    print(numbers.prefix(3))
    print(numbers.suffix(3))
    print(numbers.prefix(while: { $0 < 4 }))
    
    // Drop
    print(numbers.dropFirst())
    print(numbers.dropLast())
    print(numbers.dropFirst(2))
    
    // Split
    print(numbers.split(separator: 3))
    
    // Joined
    let words = ["Hello", "World"]
    print(words.joined(separator: " "))
}
```

## 6. Object-Oriented Programming

### Structures and Classes

```swift
// Structure (value type)
struct Point {
    var x: Int
    var y: Int
    
    // Memberwise initializer provided automatically
    // init(x: Int, y: Int) { ... }
    
    // Methods
    func distance(to other: Point) -> Double {
        let dx = Double(x - other.x)
        let dy = Double(y - other.y)
        return sqrt(dx * dx + dy * dy)
    }
    
    // Mutating method
    mutating func moveBy(x deltaX: Int, y deltaY: Int) {
        x += deltaX
        y += deltaY
    }
    
    // Static method
    static func zero() -> Point {
        Point(x: 0, y: 0)
    }
}

// Class (reference type)
class Person {
    var name: String
    var age: Int
    
    // Designated initializer
    init(name: String, age: Int) {
        self.name = name
        self.age = age
    }
    
    // Convenience initializer
    convenience init(name: String) {
        self.init(name: name, age: 0)
    }
    
    // Methods
    func greet() {
        print("Hello, I'm \(name)")
    }
    
    // Deinitializer
    deinit {
        print("\(name) is being deinitialized")
    }
}

// Value vs Reference semantics
func valueVsReference() {
    // Structs are copied
    var point1 = Point(x: 1, y: 2)
    var point2 = point1
    point2.x = 10
    print(point1.x) // 1 (unchanged)
    
    // Classes are referenced
    let person1 = Person(name: "Alice", age: 30)
    let person2 = person1
    person2.name = "Bob"
    print(person1.name) // "Bob" (changed)
}

// Identity vs Equality
func identityDemo() {
    let person1 = Person(name: "Alice", age: 30)
    let person2 = Person(name: "Alice", age: 30)
    let person3 = person1
    
    print(person1 === person3)  // true (same instance)
    print(person1 === person2)  // false (different instances)
}
```

### Properties and Methods

```swift
struct Rectangle {
    var width: Double
    var height: Double
    
    // Stored properties
    var color: String = "white"
    
    // Computed property
    var area: Double {
        width * height
    }
    
    var perimeter: Double {
        get {
            2 * (width + height)
        }
    }
    
    // Read-write computed property
    var aspectRatio: Double {
        get {
            width / height
        }
        set {
            width = height * newValue
        }
    }
    
    // Property observers
    var scale: Double = 1.0 {
        willSet {
            print("Will change to \(newValue)")
        }
        didSet {
            print("Changed from \(oldValue)")
        }
    }
    
    // Lazy property
    lazy var description: String = {
        "Rectangle of \(width) x \(height)"
    }()
    
    // Type property
    static let defaultColor = "white"
    
    // Instance method
    func describe() {
        print("Rectangle: \(width) x \(height)")
    }
    
    // Mutating method
    mutating func resize(by factor: Double) {
        width *= factor
        height *= factor
    }
    
    // Type method
    static func square(side: Double) -> Rectangle {
        Rectangle(width: side, height: side)
    }
}

// Property wrappers
@propertyWrapper
struct Clamped<Value: Comparable> {
    private var value: Value
    private let range: ClosedRange<Value>
    
    init(wrappedValue: Value, _ range: ClosedRange<Value>) {
        self.range = range
        self.value = max(range.lowerBound, min(range.upperBound, wrappedValue))
    }
    
    var wrappedValue: Value {
        get { value }
        set { value = max(range.lowerBound, min(range.upperBound, newValue)) }
    }
}

struct Game {
    @Clamped(0...100) var health = 100
    @Clamped(0...100) var stamina = 100
}
```

### Inheritance

```swift
// Base class
class Animal {
    var name: String
    
    init(name: String) {
        self.name = name
    }
    
    func makeSound() {
        print("Some generic sound")
    }
    
    func eat() {
        print("\(name) is eating")
    }
}

// Derived class
class Dog: Animal {
    var breed: String
    
    init(name: String, breed: String) {
        self.breed = breed
        super.init(name: name)
    }
    
    // Override method
    override func makeSound() {
        print("\(name) barks: Woof!")
    }
    
    // New method
    func fetch() {
        print("\(name) is fetching")
    }
}

class Cat: Animal {
    override func makeSound() {
        print("\(name) meows")
    }
    
    func scratch() {
        print("\(name) is scratching")
    }
}

// Preventing overrides
class FinalClass {
    final func cannotOverride() {}
}

// Type checking
func typeCheckingDemo() {
    let dog: Animal = Dog(name: "Buddy", breed: "Golden")
    
    if dog is Dog {
        print("It's a dog")
    }
    
    if let specificDog = dog as? Dog {
        print("Breed: \(specificDog.breed)")
    }
    
    let definiteDog = dog as! Dog // Force cast
}
```

### Protocols

```swift
// Basic protocol
protocol Drawable {
    func draw()
}

protocol Movable {
    var position: (x: Double, y: Double) { get set }
    func move(to point: (x: Double, y: Double))
}

// Conforming to protocols
struct GameObject: Drawable, Movable {
    var position: (x: Double, y: Double) = (0, 0)
    
    func draw() {
        print("Drawing at \(position)")
    }
    
    func move(to point: (x: Double, y: Double)) {
        position = point
    }
}

// Protocol with associated type
protocol Container {
    associatedtype Item
    mutating func append(_ item: Item)
    var count: Int { get }
    subscript(i: Int) -> Item { get }
}

struct IntStack: Container {
    typealias Item = Int
    
    private var items: [Int] = []
    
    mutating func append(_ item: Int) {
        items.append(item)
    }
    
    var count: Int {
        items.count
    }
    
    subscript(i: Int) -> Int {
        items[i]
    }
}

// Protocol inheritance
protocol Printable {
    func printDescription()
}

protocol Identifiable: Printable {
    var id: String { get }
}

// Protocol composition
func process(_ item: Drawable & Movable) {
    item.draw()
    item.move(to: (10, 20))
}

// Optional protocol requirements
@objc protocol DataSource {
    @objc optional func numberOfItems() -> Int
    @objc optional func itemAt(index: Int) -> String
}
```

### Extensions

```swift
// Basic extension
extension Int {
    func squared() -> Int {
        self * self
    }
    
    var isEven: Bool {
        self % 2 == 0
    }
}

print(5.squared())
print(4.isEven)

// Extension with protocol conformance
extension Array: Printable {
    func printDescription() {
        print("Array with \(count) elements")
    }
}

// Extension with generic constraints
extension Array where Element: Numeric {
    func sum() -> Element {
        reduce(0, +)
    }
}

print([1, 2, 3, 4, 5].sum())

// Extension for protocol
protocol Named {
    var name: String { get }
}

extension Named {
    func greet() {
        print("Hello, \(name)!")
    }
}
```

### Generics

```swift
// Generic function
func swapValues<T>(_ a: inout T, _ b: inout T) {
    let temp = a
    a = b
    b = temp
}

// Generic type
struct Stack<Element> {
    private var items: [Element] = []
    
    mutating func push(_ item: Element) {
        items.append(item)
    }
    
    mutating func pop() -> Element? {
        items.popLast()
    }
    
    func peek() -> Element? {
        items.last
    }
    
    var isEmpty: Bool {
        items.isEmpty
    }
}

var intStack = Stack<Int>()
intStack.push(1)
intStack.push(2)

// Generic constraints
func findIndex<T: Equatable>(of value: T, in array: [T]) -> Int? {
    for (index, element) in array.enumerated() {
        if element == value {
            return index
        }
    }
    return nil
}

// Associated types with constraints
protocol Summable {
    static func +(lhs: Self, rhs: Self) -> Self
}

extension Int: Summable {}
extension Double: Summable {}

func sum<T: Summable>(_ items: [T]) -> T? {
    guard let first = items.first else { return nil }
    return items.dropFirst().reduce(first, +)
}

// Generic where clauses
extension Stack where Element: Equatable {
    func contains(_ item: Element) -> Bool {
        items.contains(item)
    }
}
```

## 7. Functional Programming Concepts

### Higher-Order Functions

```swift
func functionalDemo() {
    let numbers = [1, 2, 3, 4, 5]
    
    // Map
    let doubled = numbers.map { $0 * 2 }
    let squared = numbers.map { $0 * $0 }
    
    // Filter
    let evens = numbers.filter { $0 % 2 == 0 }
    let greaterThanTwo = numbers.filter { $0 > 2 }
    
    // Reduce
    let sum = numbers.reduce(0, +)
    let product = numbers.reduce(1, *)
    
    // CompactMap (filter nil)
    let optionals: [Int?] = [1, nil, 3, nil, 5]
    let values = optionals.compactMap { $0 }
    
    // FlatMap
    let nested = [[1, 2], [3, 4], [5]]
    let flattened = nested.flatMap { $0 }
    
    // Chaining
    let result = numbers
        .filter { $0 % 2 == 0 }
        .map { $0 * $0 }
        .reduce(0, +)
    
    // Sorted
    let sorted = numbers.sorted()
    let sortedDesc = numbers.sorted(by: >)
    
    // First, contains
    let first = numbers.first(where: { $0 > 3 })
    let contains = numbers.contains(where: { $0 > 3 })
    
    // AllSatisfy
    let allPositive = numbers.allSatisfy { $0 > 0 }
}
```

### Function Composition

```swift
// Function composition
func compose<A, B, C>(
    _ f: @escaping (B) -> C,
    _ g: @escaping (A) -> B
) -> (A) -> C {
    { a in f(g(a)) }
}

let addOne: (Int) -> Int = { $0 + 1 }
let double: (Int) -> Int = { $0 * 2 }
let square: (Int) -> Int = { $0 * $0 }

let doubleThenSquare = compose(square, double)
print(doubleThenSquare(3)) // (3 * 2)^2 = 36

// Pipe operator simulation
infix operator |> : MultiplicationPrecedence

func |> <T, U>(value: T, transform: (T) -> U) -> U {
    transform(value)
}

let result = 5 |> addOne |> double |> square
print(result) // ((5 + 1) * 2)^2 = 144
```

### Partial Application and Currying

```swift
// Currying
func add(_ a: Int) -> (Int) -> Int {
    { b in a + b }
}

let add5 = add(5)
print(add5(3))  // 8
print(add5(10)) // 15

// Multi-parameter currying
func multiply(_ a: Int) -> (Int) -> (Int) -> Int {
    { b in { c in a * b * c } }
}

let mult2 = multiply(2)
let mult2And3 = mult2(3)
print(mult2And3(4)) // 24

// Partial application with closures
func greet(greeting: String, name: String) -> String {
    "\(greeting), \(name)!"
}

let sayHello = { (name: String) in greet(greeting: "Hello", name: name) }
let sayHi = { (name: String) in greet(greeting: "Hi", name: name) }

print(sayHello("Alice"))  // Hello, Alice!
print(sayHi("Bob"))       // Hi, Bob!
```

### Immutability

```swift
// Immutable by default with let
let immutableArray = [1, 2, 3]
// immutableArray.append(4) // Error

// Functional array operations (return new arrays)
let original = [1, 2, 3]
let withFour = original + [4]
let doubled = original.map { $0 * 2 }
let evens = original.filter { $0 % 2 == 0 }

print(original)  // [1, 2, 3]
print(withFour)  // [1, 2, 3, 4]

// Immutable value types
struct Point {
    let x: Int
    let y: Int
    
    func moved(x dx: Int, y dy: Int) -> Point {
        Point(x: x + dx, y: y + dy)
    }
}

let point = Point(x: 1, y: 2)
let movedPoint = point.moved(x: 2, y: 3)
print(point)       // Point(x: 1, y: 2)
print(movedPoint)  // Point(x: 3, y: 5)
```

### Monads and Functors

```swift
// Optional is a monad
let value: Int? = 42

// Functor (map)
let doubled = value.map { $0 * 2 }

// Monad (flatMap)
func divide(_ a: Int, by b: Int) -> Int? {
    b == 0 ? nil : a / b
}

let result = value.flatMap { divide($0, by: 2) }

// Result type
enum Result<Success, Failure: Error> {
    case success(Success)
    case failure(Failure)
    
    func map<U>(_ transform: (Success) -> U) -> Result<U, Failure> {
        switch self {
        case .success(let value):
            return .success(transform(value))
        case .failure(let error):
            return .failure(error)
        }
    }
    
    func flatMap<U>(_ transform: (Success) -> Result<U, Failure>) -> Result<U, Failure> {
        switch self {
        case .success(let value):
            return transform(value)
        case .failure(let error):
            return .failure(error)
        }
    }
}
```

## 8. Memory Management

### Automatic Reference Counting (ARC)

```swift
class Person {
    let name: String
    
    init(name: String) {
        self.name = name
        print("\(name) is initialized")
    }
    
    deinit {
        print("\(name) is being deinitialized")
    }
}

func arcDemo() {
    var person1: Person? = Person(name: "Alice")
    var person2: Person? = person1
    var person3: Person? = person1
    
    // Reference count is 3
    
    person1 = nil  // Count: 2
    person2 = nil  // Count: 1
    person3 = nil  // Count: 0, deinitialized
}

// Strong reference cycles
class Apartment {
    let unit: String
    var tenant: Person?
    
    init(unit: String) {
        self.unit = unit
    }
    
    deinit {
        print("Apartment \(unit) is being deinitialized")
    }
}

// Weak references
class Person2 {
    let name: String
    var apartment: Apartment?
    
    init(name: String) {
        self.name = name
    }
    
    deinit {
        print("\(name) is being deinitialized")
    }
}

class Apartment2 {
    let unit: String
    weak var tenant: Person2?  // Weak reference
    
    init(unit: String) {
        self.unit = unit
    }
    
    deinit {
        print("Apartment \(unit) is being deinitialized")
    }
}

// Unowned references
class Customer {
    let name: String
    var card: CreditCard?
    
    init(name: String) {
        self.name = name
    }
    
    deinit {
        print("\(name) is being deinitialized")
    }
}

class CreditCard {
    let number: UInt64
    unowned let customer: Customer  // Unowned reference
    
    init(number: UInt64, customer: Customer) {
        self.number = number
        self.customer = customer
    }
    
    deinit {
        print("Card #\(number) is being deinitialized")
    }
}

// Closures and capture lists
class HTMLElement {
    let name: String
    let text: String?
    
    lazy var asHTML: () -> String = { [unowned self] in
        if let text = self.text {
            return "<\(self.name)>\(text)</\(self.name)>"
        } else {
            return "<\(self.name) />"
        }
    }
    
    init(name: String, text: String? = nil) {
        self.name = name
        self.text = text
    }
    
    deinit {
        print("\(name) is being deinitialized")
    }
}
```

### Value Types vs Reference Types

```swift
// Value types (struct, enum) are copied
struct ValueType {
    var value: Int
}

var value1 = ValueType(value: 42)
var value2 = value1
value2.value = 10

print(value1.value) // 42 (unchanged)
print(value2.value) // 10

// Reference types (class) are referenced
class ReferenceType {
    var value: Int
    init(value: Int) { self.value = value }
}

let ref1 = ReferenceType(value: 42)
let ref2 = ref1
ref2.value = 10

print(ref1.value) // 10 (changed)
print(ref2.value) // 10

// Copy-on-write for collections
var array1 = [1, 2, 3]
var array2 = array1  // Shares storage
array2.append(4)     // Now copied

print(array1) // [1, 2, 3]
print(array2) // [1, 2, 3, 4]
```

## 9. Standard Library

### String Manipulation

```swift
func stringLibraryDemo() {
    let str = "Hello, Swift!"
    
    // Properties
    print(str.count)
    print(str.isEmpty)
    
    // Case conversion
    print(str.uppercased())
    print(str.lowercased())
    
    // Prefix and suffix
    print(str.hasPrefix("Hello"))
    print(str.hasSuffix("!"))
    print(str.hasPrefix("swift".capitalized))
    
    // Contains
    print(str.contains("Swift"))
    
    // Split and join
    let words = str.split(separator: ",")
    let joined = words.joined(separator: " and")
    
    // Trim
    let trimmed = "  hello  ".trimmingCharacters(in: .whitespaces)
    
    // Replace
    let replaced = str.replacingOccurrences(of: "Swift", with: "World")
    
    // Substring
    let index = str.index(str.startIndex, offsetBy: 7)
    let substring = str[index...]
    
    // Iteration
    for char in str {
        print(char)
    }
    
    // Unicode
    for scalar in str.unicodeScalars {
        print(scalar.value)
    }
}
```

### Collection Algorithms

```swift
import Foundation

func collectionAlgorithmsDemo() {
    let numbers = [1, 2, 3, 4, 5]
    
    // Transformations
    numbers.map { $0 * 2 }
    numbers.filter { $0 % 2 == 0 }
    numbers.reduce(0, +)
    
    // Sorting
    numbers.sorted()
    numbers.sorted(by: >)
    
    // Min, max
    numbers.min()
    numbers.max()
    
    // First, last
    numbers.first
    numbers.last
    numbers.first(where: { $0 > 3 })
    
    // Prefix, suffix
    numbers.prefix(3)
    numbers.suffix(3)
    numbers.prefix(while: { $0 < 4 })
    
    // Drop
    numbers.dropFirst()
    numbers.dropLast()
    numbers.drop(while: { $0 < 3 })
    
    // Split
    numbers.split(separator: 3)
    
    // Enumerated
    for (index, value) in numbers.enumerated() {
        print("\(index): \(value)")
    }
    
    // Shuffled
    numbers.shuffled()
    
    // Reversed
    numbers.reversed()
}
```

### Foundation Framework

```swift
import Foundation

func foundationDemo() {
    // Date and Time
    let now = Date()
    let calendar = Calendar.current
    let components = calendar.dateComponents([.year, .month, .day], from: now)
    
    let formatter = DateFormatter()
    formatter.dateStyle = .medium
    print(formatter.string(from: now))
    
    // URL
    let url = URL(string: "https://example.com/api")!
    print(url.scheme)
    print(url.host)
    print(url.path)
    
    // Data
    let data = "Hello".data(using: .utf8)!
    let string = String(data: data, encoding: .utf8)
    
    // JSON
    struct User: Codable {
        let name: String
        let age: Int
    }
    
    let user = User(name: "Alice", age: 30)
    let encoder = JSONEncoder()
    let jsonData = try! encoder.encode(user)
    
    let decoder = JSONDecoder()
    let decodedUser = try! decoder.decode(User.self, from: jsonData)
    
    // FileManager
    let fileManager = FileManager.default
    let documentsURL = fileManager.urls(for: .documentDirectory, in: .userDomainMask).first!
    
    // UserDefaults
    let defaults = UserDefaults.standard
    defaults.set("value", forKey: "key")
    let value = defaults.string(forKey: "key")
    
    // Timer
    let timer = Timer.scheduledTimer(withTimeInterval: 1.0, repeats: true) { timer in
        print("Timer fired")
    }
    // timer.invalidate()
}
```

## 10. Tooling and Ecosystem

### Swift Package Manager

```swift
// Package.swift
// swift-tools-version:5.5
import PackageDescription

let package = Package(
    name: "MyPackage",
    platforms: [
        .macOS(.v11),
        .iOS(.v14)
    ],
    products: [
        .library(
            name: "MyPackage",
            targets: ["MyPackage"]),
    ],
    dependencies: [
        .package(url: "https://github.com/apple/swift-nio.git", from: "2.0.0"),
    ],
    targets: [
        .target(
            name: "MyPackage",
            dependencies: [
                .product(name: "NIO", package: "swift-nio")
            ]),
        .testTarget(
            name: "MyPackageTests",
            dependencies: ["MyPackage"]),
    ]
)
```

### Testing

```swift
import XCTest

class CalculatorTests: XCTestCase {
    func testAddition() {
        let result = 2 + 3
        XCTAssertEqual(result, 5)
    }
    
    func testSubtraction() {
        let result = 5 - 3
        XCTAssertEqual(result, 2)
    }
    
    func testDivisionByZero() {
        XCTAssertThrowsError(try divide(10, by: 0))
    }
    
    func testOptional() {
        let value: Int? = 42
        XCTAssertNotNil(value)
        XCTAssertEqual(value, 42)
    }
    
    // Async test (Swift 5.5+)
    func testAsync() async throws {
        let result = try await fetchData()
        XCTAssertEqual(result, "data")
    }
}

func divide(_ a: Int, by b: Int) throws -> Int {
    guard b != 0 else {
        throw NSError(domain: "DivisionError", code: 1)
    }
    return a / b
}

func fetchData() async throws -> String {
    try await Task.sleep(nanoseconds: 100_000_000)
    return "data"
}
```

## 11. Best Practices

### Code Style

```swift
// Use meaningful names
func calculateArea(width: Double, height: Double) -> Double {
    width * height
}

// Use type inference
let name = "Alice"  // Not: let name: String = "Alice"

// Use shorthand
let doubled = numbers.map { $0 * 2 }

// Guard for early exit
func greet(name: String?) {
    guard let name = name else {
        return
    }
    print("Hello, \(name)!")
}

// Use extensions for organization
extension String {
    var isEmail: Bool {
        contains("@")
    }
}

// Protocol-oriented programming
protocol Drawable {
    func draw()
}

extension Drawable {
    func draw() {
        print("Drawing...")
    }
}

// Use value types when possible
struct Point {  // Not class
    let x: Int
    let y: Int
}

// Avoid force unwrapping
if let value = optional {
    // Use value
}

// Use guard for multiple optionals
guard let name = name,
      let age = age,
      age > 0 else {
    return
}
```

### Safety

```swift
// Optional safety
func safeDivide(_ a: Int, by b: Int) -> Int? {
    guard b != 0 else { return nil }
    return a / b
}

// Error handling
enum NetworkError: Error {
    case noConnection
    case timeout
}

func fetchData() throws -> String {
    throw NetworkError.noConnection
}

// Result type
func fetchDataResult() -> Result<String, NetworkError> {
    .failure(.noConnection)
}

// Memory safety
class Parent {
    var child: Child?
    deinit { print("Parent deinitialized") }
}

class Child {
    weak var parent: Parent?
    deinit { print("Child deinitialized") }
}
```

### Performance

```swift
// Use lazy properties
class DataManager {
    lazy var data = loadExpensiveData()
    
    func loadExpensiveData() -> [String] {
        // Expensive operation
        return []
    }
}

// Use value types for better performance
struct Point {  // Allocated on stack
    let x: Int
    let y: Int
}

// Avoid unnecessary copies
func process(_ array: inout [Int]) {
    // Modify in place
    array.append(1)
}

// Use lazy collections
let numbers = 1...1_000_000
let result = numbers.lazy
    .filter { $0 % 2 == 0 }
    .map { $0 * 2 }
    .prefix(10)
```

## 12. Conclusion

### Key Takeaways

Swift is a modern, powerful programming language that offers:

1. **Safety**: Type safety, optionals, memory management
2. **Performance**: As fast as C-based languages
3. **Expressiveness**: Clean, readable syntax
4. **Modern Features**: Generics, protocols, async/await
5. **Apple Ecosystem**: Primary language for iOS/macOS
6. **Open Source**: Cross-platform development
7. **Growing Community**: Active and supportive

### Learning Path

1. **Basics**: Master syntax, types, optionals
2. **Collections**: Arrays, sets, dictionaries
3. **Functions**: Closures, higher-order functions
4. **OOP**: Classes, structs, protocols
5. **Generics**: Type-safe generic code
6. **Error Handling**: Safe error management
7. **Concurrency**: Async/await, actors
8. **SwiftUI**: Modern UI framework
9. **Combine**: Reactive programming
10. **Testing**: XCTest framework

### Resources

- **Official Docs**: swift.org
- **Swift Book**: docs.swift.org/swift-book
- **Apple Developer**: developer.apple.com
- **Swift Forums**: forums.swift.org
- **Ray Wenderlich**: raywenderlich.com

### Next Steps

1. Build iOS/macOS apps
2. Learn SwiftUI and Combine
3. Explore server-side Swift (Vapor)
4. Study design patterns
5. Contribute to open source
6. Join the Swift community
7. Build portfolio projects

This guide covers essential Swift programming concepts. Continue practicing and building projects to master the language and the Apple ecosystem!
