# Dart Programming Language Proficiency Guide

## 1. Introduction

Dart is a client-optimized programming language developed by Google for building fast apps on any platform. Originally designed for web development, Dart has evolved into a powerful language for mobile, desktop, server, and web applications, particularly through the Flutter framework.

### Key Characteristics

- **Strongly typed**: With sound null safety
- **Object-oriented**: Everything is an object
- **Multi-paradigm**: Supports OOP, functional, and imperative programming
- **Compiled and interpreted**: Can be AOT or JIT compiled
- **Modern syntax**: Clean, familiar syntax similar to C-style languages

### Why Learn Dart?

- **Flutter development**: Primary language for Flutter mobile/desktop apps
- **Performance**: Fast execution with ahead-of-time compilation
- **Productivity**: Hot reload, rich standard library, and modern features
- **Versatility**: Write once, deploy everywhere (mobile, web, desktop, server)

### Setting Up Dart

```bash
# Install Dart SDK
# macOS
brew tap dart-lang/dart
brew install dart

# Windows (using Chocolatey)
choco install dart-sdk

# Linux
sudo apt-get update
sudo apt-get install dart

# Verify installation
dart --version
```

### Hello World

```dart
// hello_world.dart
void main() {
  print('Hello, Dart!');
}
```

Run with:
```bash
dart run hello_world.dart
```

## 2. Core Language Mechanics

### Syntax Fundamentals

```dart
// Single-line comment
/* Multi-line
   comment */

/// Documentation comment
/// Used for generating API docs

// Statements end with semicolons
var message = 'Hello';
print(message);

// Code blocks use curly braces
if (true) {
  print('Block statement');
}
```

### Variables and Constants

```dart
void variablesDemo() {
  // var - type inference
  var name = 'Alice';
  var age = 30;
  
  // Explicit types
  String city = 'New York';
  int population = 8000000;
  double temperature = 72.5;
  bool isCapital = false;
  
  // Dynamic type (avoid when possible)
  dynamic flexibleVar = 'string';
  flexibleVar = 42; // Can change type
  
  // Final - runtime constant
  final currentTime = DateTime.now();
  // currentTime = DateTime.now(); // ERROR: can't reassign
  
  // Const - compile-time constant
  const pi = 3.14159;
  const appName = 'MyApp';
  // const now = DateTime.now(); // ERROR: must be compile-time constant
  
  // Late initialization
  late String description;
  description = 'Set later'; // Must be set before use
  print(description);
}
```

### Data Types

```dart
void dataTypesDemo() {
  // Numbers
  int integer = 42;
  int hexValue = 0xDEADBEEF;
  int bigInt = 9223372036854775807; // 64-bit
  
  double decimal = 3.14;
  double exponent = 1.42e5;
  
  // Strings
  String singleQuote = 'Single quotes';
  String doubleQuote = "Double quotes";
  String multiLine = '''
    Multiple
    lines
    supported
  ''';
  
  // String interpolation
  var name = 'Alice';
  var age = 30;
  print('$name is $age years old');
  print('Next year: ${age + 1}');
  
  // Raw strings
  String rawString = r'No interpretation: \n $name';
  
  // Booleans
  bool isTrue = true;
  bool isFalse = false;
  
  // Runes (Unicode code points)
  var heart = '\u2665';
  var laughing = '\u{1f600}';
  
  // Symbols
  Symbol sym = #mySymbol;
}
```

### Null Safety

```dart
void nullSafetyDemo() {
  // Non-nullable by default
  String name = 'Alice';
  // name = null; // ERROR: can't assign null
  
  // Nullable type
  String? nullableName;
  nullableName = null; // OK
  nullableName = 'Bob'; // OK
  
  // Null-aware operators
  String? userName;
  
  // ?? - null coalescing
  String displayName = userName ?? 'Guest';
  
  // ??= - null-aware assignment
  userName ??= 'DefaultUser';
  
  // ?. - null-aware access
  int? length = userName?.length;
  
  // ! - null assertion (use with caution)
  String definiteName = userName!; // Throws if null
  
  // Late variables
  late String lateInit;
  // print(lateInit); // ERROR: used before initialization
  lateInit = 'Now initialized';
  print(lateInit); // OK
}
```

### Operators

```dart
void operatorsDemo() {
  // Arithmetic
  print(5 + 3);  // 8
  print(5 - 3);  // 2
  print(5 * 3);  // 15
  print(5 / 3);  // 1.6666...
  print(5 ~/ 3); // 1 (integer division)
  print(5 % 3);  // 2 (modulo)
  
  // Increment/Decrement
  var a = 5;
  print(++a); // 6 (pre-increment)
  print(a++); // 6 (post-increment)
  print(a);   // 7
  
  // Relational
  print(5 == 3);  // false
  print(5 != 3);  // true
  print(5 > 3);   // true
  print(5 < 3);   // false
  print(5 >= 3);  // true
  print(5 <= 3);  // false
  
  // Logical
  print(true && false);  // false
  print(true || false);  // true
  print(!true);          // false
  
  // Bitwise
  print(5 & 3);   // 1 (AND)
  print(5 | 3);   // 7 (OR)
  print(5 ^ 3);   // 6 (XOR)
  print(~5);      // -6 (NOT)
  print(5 << 1);  // 10 (left shift)
  print(5 >> 1);  // 2 (right shift)
  
  // Type test
  var obj = 'string';
  print(obj is String);     // true
  print(obj is! int);       // true
  
  // Type cast
  var number = obj as String; // Succeeds
  
  // Assignment
  var x = 5;
  x += 3;  // x = x + 3
  x -= 2;  // x = x - 2
  x *= 2;  // x = x * 2
  x ~/= 2; // x = x ~/ 2
  
  // Conditional
  var result = x > 5 ? 'big' : 'small';
  
  // Cascade notation
  var list = <int>[]
    ..add(1)
    ..add(2)
    ..add(3);
  print(list); // [1, 2, 3]
  
  // Spread operator
  var list1 = [1, 2, 3];
  var list2 = [0, ...list1, 4]; // [0, 1, 2, 3, 4]
  
  // Null-aware spread
  List<int>? nullableList;
  var list3 = [0, ...?nullableList]; // [0]
}
```

### Type System

```dart
void typeSystemDemo() {
  // Type inference
  var inferred = 'Hello'; // String
  var number = 42;        // int
  
  // Generic types
  List<String> names = ['Alice', 'Bob'];
  Map<String, int> ages = {'Alice': 30, 'Bob': 25};
  
  // Type promotion
  Object obj = 'Hello';
  if (obj is String) {
    // obj is promoted to String within this block
    print(obj.length);
  }
  
  // Function types
  typedef IntOperation = int Function(int, int);
  
  IntOperation add = (a, b) => a + b;
  IntOperation multiply = (a, b) => a * b;
  
  print(add(5, 3));      // 8
  print(multiply(5, 3)); // 15
}
```

## 3. Control Flow

### Conditional Statements

```dart
void conditionalsDemo() {
  // if-else
  var age = 20;
  if (age < 18) {
    print('Minor');
  } else if (age < 65) {
    print('Adult');
  } else {
    print('Senior');
  }
  
  // Single-line if
  if (age >= 18) print('Can vote');
  
  // Ternary operator
  String status = age >= 18 ? 'Adult' : 'Minor';
  
  // Switch statement
  var grade = 'B';
  switch (grade) {
    case 'A':
      print('Excellent');
      break;
    case 'B':
      print('Good');
      break;
    case 'C':
      print('Average');
      break;
    default:
      print('Keep trying');
  }
  
  // Switch with enums
  enum Status { pending, approved, rejected }
  
  var requestStatus = Status.approved;
  switch (requestStatus) {
    case Status.pending:
      print('Waiting for approval');
      break;
    case Status.approved:
      print('Request approved');
      break;
    case Status.rejected:
      print('Request rejected');
      break;
  }
  
  // Switch with continue
  var command = 'CLOSED';
  switch (command) {
    case 'CLOSED':
      print('Closed');
      continue nowClosed;
    
    nowClosed:
    case 'NOW_CLOSED':
      print('Now closed');
      break;
  }
}
```

### Loops

```dart
void loopsDemo() {
  // For loop
  for (var i = 0; i < 5; i++) {
    print('Iteration $i');
  }
  
  // For-in loop
  var fruits = ['apple', 'banana', 'orange'];
  for (var fruit in fruits) {
    print(fruit);
  }
  
  // While loop
  var count = 0;
  while (count < 5) {
    print('Count: $count');
    count++;
  }
  
  // Do-while loop
  var num = 0;
  do {
    print('Number: $num');
    num++;
  } while (num < 5);
  
  // Break and continue
  for (var i = 0; i < 10; i++) {
    if (i == 3) continue; // Skip 3
    if (i == 7) break;    // Stop at 7
    print(i);
  }
  
  // Nested loops with labels
  outerLoop:
  for (var i = 0; i < 3; i++) {
    for (var j = 0; j < 3; j++) {
      if (i == 1 && j == 1) break outerLoop;
      print('$i, $j');
    }
  }
  
  // Collection iteration
  var numbers = [1, 2, 3, 4, 5];
  
  // forEach
  numbers.forEach((num) => print(num));
  
  // for-in with index
  for (var i = 0; i < numbers.length; i++) {
    print('Index $i: ${numbers[i]}');
  }
  
  // Using indexed iteration
  numbers.asMap().forEach((index, value) {
    print('$index: $value');
  });
}
```

### Exception Handling

```dart
// Custom exceptions
class InvalidAgeException implements Exception {
  final String message;
  InvalidAgeException(this.message);
  
  @override
  String toString() => 'InvalidAgeException: $message';
}

class ValidationException implements Exception {
  final String field;
  final String reason;
  
  ValidationException(this.field, this.reason);
  
  @override
  String toString() => 'ValidationException: $field - $reason';
}

void exceptionHandlingDemo() {
  // Basic try-catch
  try {
    var result = 12 ~/ 0;
    print(result);
  } catch (e) {
    print('Error: $e');
  }
  
  // Catch specific exception
  try {
    throw FormatException('Invalid format');
  } on FormatException catch (e) {
    print('Format error: $e');
  }
  
  // Multiple catch blocks
  try {
    // Some operation
    throw ArgumentError('Invalid argument');
  } on FormatException catch (e) {
    print('Format error: $e');
  } on ArgumentError catch (e) {
    print('Argument error: $e');
  } catch (e) {
    print('Unknown error: $e');
  }
  
  // Stack trace
  try {
    throw Exception('Something went wrong');
  } catch (e, stackTrace) {
    print('Error: $e');
    print('Stack trace: $stackTrace');
  }
  
  // Finally block
  try {
    print('Attempting operation');
    throw Exception('Operation failed');
  } catch (e) {
    print('Caught: $e');
  } finally {
    print('Cleanup code runs regardless');
  }
  
  // Rethrowing exceptions
  try {
    try {
      throw Exception('Original error');
    } catch (e) {
      print('Caught and rethrowing');
      rethrow;
    }
  } catch (e) {
    print('Caught rethrown exception: $e');
  }
  
  // Custom exceptions
  try {
    validateAge(-5);
  } on InvalidAgeException catch (e) {
    print(e);
  }
  
  // Using assertions
  var age = 20;
  assert(age >= 0, 'Age must be non-negative');
  // Assertions only run in debug mode
}

void validateAge(int age) {
  if (age < 0) {
    throw InvalidAgeException('Age cannot be negative');
  }
}

// Error handling patterns
Future<int> fetchData() async {
  try {
    // Simulate network call
    await Future.delayed(Duration(seconds: 1));
    throw Exception('Network error');
  } catch (e) {
    print('Error fetching data: $e');
    rethrow;
  }
}

void errorHandlingPatterns() async {
  // Try-catch with async
  try {
    var data = await fetchData();
    print(data);
  } catch (e) {
    print('Handled error: $e');
  }
}
```

## 4. Functions and Code Organization

### Function Basics

```dart
// Basic function
int add(int a, int b) {
  return a + b;
}

// Single expression (arrow syntax)
int multiply(int a, int b) => a * b;

// Void function
void greet(String name) {
  print('Hello, $name!');
}

// Optional positional parameters
String formatName(String first, [String? middle, String? last]) {
  var result = first;
  if (middle != null) result += ' $middle';
  if (last != null) result += ' $last';
  return result;
}

// Default parameter values
int power(int base, [int exponent = 2]) {
  var result = 1;
  for (var i = 0; i < exponent; i++) {
    result *= base;
  }
  return result;
}

// Named parameters
void createUser({
  required String name,
  required String email,
  int age = 0,
  String? phone,
}) {
  print('Name: $name');
  print('Email: $email');
  print('Age: $age');
  if (phone != null) print('Phone: $phone');
}

// Mixed positional and named parameters
void logMessage(String message, {String level = 'INFO', DateTime? timestamp}) {
  var time = timestamp ?? DateTime.now();
  print('[$level] $time: $message');
}

void functionsDemo() {
  // Calling functions
  print(add(5, 3));              // 8
  print(multiply(4, 7));         // 28
  greet('Alice');                // Hello, Alice!
  
  // Optional parameters
  print(formatName('John'));              // John
  print(formatName('John', 'Q'));         // John Q
  print(formatName('John', 'Q', 'Doe'));  // John Q Doe
  
  // Default values
  print(power(2));      // 4 (2^2)
  print(power(2, 3));   // 8 (2^3)
  
  // Named parameters
  createUser(name: 'Alice', email: 'alice@example.com');
  createUser(
    name: 'Bob',
    email: 'bob@example.com',
    age: 30,
    phone: '555-1234',
  );
  
  // Mixed parameters
  logMessage('Application started');
  logMessage('Error occurred', level: 'ERROR');
}
```

### Higher-Order Functions

```dart
// Function as parameter
void executeOperation(int a, int b, Function(int, int) operation) {
  print('Result: ${operation(a, b)}');
}

// Function returning function
Function makeAdder(int addBy) {
  return (int value) => value + addBy;
}

// Generic function types
typedef Predicate<T> = bool Function(T);
typedef Transformer<T, R> = R Function(T);

void higherOrderDemo() {
  // Pass function as argument
  executeOperation(5, 3, (a, b) => a + b);
  executeOperation(5, 3, (a, b) => a * b);
  
  // Return function
  var add5 = makeAdder(5);
  print(add5(10)); // 15
  print(add5(20)); // 25
  
  // Store function in variable
  var calculator = add;
  print(calculator(3, 4)); // 7
  
  // Anonymous functions
  var numbers = [1, 2, 3, 4, 5];
  
  var doubled = numbers.map((n) => n * 2).toList();
  print(doubled); // [2, 4, 6, 8, 10]
  
  var evens = numbers.where((n) => n % 2 == 0).toList();
  print(evens); // [2, 4]
  
  var sum = numbers.reduce((a, b) => a + b);
  print(sum); // 15
  
  // Using typedef
  Predicate<int> isEven = (n) => n % 2 == 0;
  Transformer<int, String> intToString = (n) => 'Number: $n';
  
  print(isEven(4));           // true
  print(intToString(42));     // Number: 42
}
```

### Closures and Lexical Scope

```dart
Function makeCounter() {
  var count = 0;
  
  return () {
    count++;
    return count;
  };
}

Function makeMultiplier(int factor) {
  return (int value) => value * factor;
}

void closuresDemo() {
  // Closure maintains state
  var counter = makeCounter();
  print(counter()); // 1
  print(counter()); // 2
  print(counter()); // 3
  
  // Another independent counter
  var counter2 = makeCounter();
  print(counter2()); // 1
  
  // Closure with parameters
  var times2 = makeMultiplier(2);
  var times10 = makeMultiplier(10);
  
  print(times2(5));   // 10
  print(times10(5));  // 50
  
  // Capturing variables
  var outerValue = 10;
  var closure = () => outerValue * 2;
  print(closure()); // 20
  
  outerValue = 20;
  print(closure()); // 40 (captures current value)
}
```

### Asynchronous Functions

```dart
// Future-based async function
Future<String> fetchUserData(int userId) async {
  // Simulate network delay
  await Future.delayed(Duration(seconds: 1));
  return 'User data for $userId';
}

// Multiple async operations
Future<void> processData() async {
  print('Starting...');
  
  var data1 = await fetchUserData(1);
  print(data1);
  
  var data2 = await fetchUserData(2);
  print(data2);
  
  print('Done!');
}

// Parallel async operations
Future<void> parallelProcessing() async {
  print('Starting parallel operations...');
  
  var results = await Future.wait([
    fetchUserData(1),
    fetchUserData(2),
    fetchUserData(3),
  ]);
  
  results.forEach(print);
  print('All done!');
}

// Stream-based async
Stream<int> countStream(int max) async* {
  for (var i = 1; i <= max; i++) {
    await Future.delayed(Duration(milliseconds: 500));
    yield i;
  }
}

Future<void> streamsDemo() async {
  // Listen to stream
  await for (var value in countStream(5)) {
    print('Received: $value');
  }
  
  // Transform stream
  var stream = countStream(5);
  var doubled = stream.map((n) => n * 2);
  
  await for (var value in doubled) {
    print('Doubled: $value');
  }
}

// Error handling in async
Future<String> fetchDataWithError() async {
  await Future.delayed(Duration(seconds: 1));
  throw Exception('Network error');
}

Future<void> asyncErrorHandling() async {
  try {
    var data = await fetchDataWithError();
    print(data);
  } catch (e) {
    print('Caught error: $e');
  }
}
```

### Generators

```dart
// Synchronous generator
Iterable<int> naturals(int n) sync* {
  var k = 0;
  while (k < n) {
    yield k++;
  }
}

// Recursive generator
Iterable<int> fibonacci(int n) sync* {
  if (n > 0) yield 0;
  if (n > 1) yield 1;
  
  if (n > 2) {
    var a = 0, b = 1;
    for (var i = 2; i < n; i++) {
      var c = a + b;
      yield c;
      a = b;
      b = c;
    }
  }
}

// Asynchronous generator
Stream<String> fetchDataStream() async* {
  for (var i = 1; i <= 5; i++) {
    await Future.delayed(Duration(seconds: 1));
    yield 'Data chunk $i';
  }
}

void generatorsDemo() {
  // Synchronous generator
  print(naturals(5).toList()); // [0, 1, 2, 3, 4]
  print(fibonacci(8).toList()); // [0, 1, 1, 2, 3, 5, 8, 13]
  
  // Using sync* generator
  for (var num in naturals(10)) {
    if (num % 2 == 0) print(num);
  }
}
```

## 5. Data Structures

### Lists

```dart
void listsDemo() {
  // Creating lists
  var list1 = [1, 2, 3, 4, 5];
  List<String> list2 = ['a', 'b', 'c'];
  var emptyList = <int>[];
  
  // Fixed-length list
  var fixedList = List<int>.filled(5, 0);
  print(fixedList); // [0, 0, 0, 0, 0]
  
  // Generate list
  var generated = List<int>.generate(5, (index) => index * 2);
  print(generated); // [0, 2, 4, 6, 8]
  
  // List operations
  var numbers = [1, 2, 3];
  numbers.add(4);              // [1, 2, 3, 4]
  numbers.addAll([5, 6]);      // [1, 2, 3, 4, 5, 6]
  numbers.insert(0, 0);        // [0, 1, 2, 3, 4, 5, 6]
  numbers.insertAll(0, [-2, -1]); // [-2, -1, 0, 1, 2, 3, 4, 5, 6]
  
  // Removing elements
  numbers.remove(0);           // Remove first occurrence
  numbers.removeAt(0);         // Remove at index
  numbers.removeLast();        // Remove last
  numbers.removeWhere((n) => n < 0); // Remove by condition
  numbers.removeRange(0, 2);   // Remove range
  
  // Accessing elements
  var fruits = ['apple', 'banana', 'cherry'];
  print(fruits[0]);            // apple
  print(fruits.first);         // apple
  print(fruits.last);          // cherry
  print(fruits.length);        // 3
  print(fruits.isEmpty);       // false
  print(fruits.isNotEmpty);    // true
  
  // List properties
  print(fruits.reversed);      // (cherry, banana, apple)
  
  // Searching
  print(fruits.contains('banana'));     // true
  print(fruits.indexOf('cherry'));      // 2
  print(fruits.lastIndexOf('apple'));   // 0
  
  // Sublist
  var sublist = fruits.sublist(1, 3);  // [banana, cherry]
  
  // List comprehension alternatives
  var nums = [1, 2, 3, 4, 5];
  
  // Map
  var doubled = nums.map((n) => n * 2).toList();
  print(doubled); // [2, 4, 6, 8, 10]
  
  // Where (filter)
  var evens = nums.where((n) => n % 2 == 0).toList();
  print(evens); // [2, 4]
  
  // Reduce
  var sum = nums.reduce((a, b) => a + b);
  print(sum); // 15
  
  // Fold
  var product = nums.fold(1, (a, b) => a * b);
  print(product); // 120
  
  // Every and Any
  print(nums.every((n) => n > 0));     // true
  print(nums.any((n) => n > 3));       // true
  
  // Sorting
  var unsorted = [3, 1, 4, 1, 5, 9, 2, 6];
  unsorted.sort();
  print(unsorted); // [1, 1, 2, 3, 4, 5, 6, 9]
  
  var words = ['banana', 'apple', 'cherry'];
  words.sort((a, b) => a.compareTo(b));
  print(words); // [apple, banana, cherry]
  
  // Spread operator
  var list3 = [1, 2, 3];
  var list4 = [0, ...list3, 4];
  print(list4); // [0, 1, 2, 3, 4]
  
  // Collection if
  var includeZero = true;
  var list5 = [
    if (includeZero) 0,
    1,
    2,
    3,
  ];
  print(list5); // [0, 1, 2, 3]
  
  // Collection for
  var list6 = [
    for (var i = 0; i < 5; i++) i * 2
  ];
  print(list6); // [0, 2, 4, 6, 8]
}
```

### Sets

```dart
void setsDemo() {
  // Creating sets
  var set1 = {1, 2, 3};
  Set<String> set2 = {'a', 'b', 'c'};
  var emptySet = <int>{};
  
  // From list
  var fromList = Set<int>.from([1, 2, 2, 3, 3, 3]);
  print(fromList); // {1, 2, 3}
  
  // Set operations
  var numbers = {1, 2, 3};
  numbers.add(4);              // {1, 2, 3, 4}
  numbers.add(3);              // {1, 2, 3, 4} (no duplicates)
  numbers.addAll({5, 6});      // {1, 2, 3, 4, 5, 6}
  
  // Removing
  numbers.remove(1);           // {2, 3, 4, 5, 6}
  numbers.removeWhere((n) => n > 4); // {2, 3, 4}
  
  // Set properties
  print(numbers.length);       // 3
  print(numbers.isEmpty);      // false
  print(numbers.contains(3));  // true
  
  // Set algebra
  var a = {1, 2, 3, 4};
  var b = {3, 4, 5, 6};
  
  // Union
  print(a.union(b));           // {1, 2, 3, 4, 5, 6}
  
  // Intersection
  print(a.intersection(b));    // {3, 4}
  
  // Difference
  print(a.difference(b));      // {1, 2}
  
  // Subset and superset
  var c = {1, 2};
  print(c.difference(a).isEmpty); // true (c is subset of a)
  
  // Converting
  var setToList = a.toList();
  var listToSet = [1, 2, 2, 3].toSet();
  
  // Iteration
  for (var num in numbers) {
    print(num);
  }
  
  numbers.forEach((num) => print(num));
}
```

### Maps

```dart
void mapsDemo() {
  // Creating maps
  var map1 = {'name': 'Alice', 'age': 30};
  Map<String, int> map2 = {'a': 1, 'b': 2, 'c': 3};
  var emptyMap = <String, int>{};
  
  // From entries
  var fromEntries = Map.fromEntries([
    MapEntry('key1', 'value1'),
    MapEntry('key2', 'value2'),
  ]);
  
  // Map operations
  var person = <String, dynamic>{};
  person['name'] = 'Bob';
  person['age'] = 25;
  person['city'] = 'New York';
  
  // Access
  print(person['name']);       // Bob
  print(person['country']);    // null (key doesn't exist)
  
  // Safe access
  var country = person['country'] ?? 'Unknown';
  
  // Properties
  print(person.length);        // 3
  print(person.isEmpty);       // false
  print(person.keys);          // (name, age, city)
  print(person.values);        // (Bob, 25, New York)
  print(person.entries);       // MapEntry pairs
  
  // Check existence
  print(person.containsKey('name'));    // true
  print(person.containsValue(25));      // true
  
  // Removing
  person.remove('city');
  person.removeWhere((k, v) => v is int && v < 30);
  
  // Update
  var scores = {'Alice': 90, 'Bob': 85};
  scores.update('Alice', (value) => value + 5); // 95
  scores.update('Charlie', (value) => value + 5, ifAbsent: () => 80);
  
  // Update all
  scores.updateAll((key, value) => value + 10);
  
  // Put if absent
  scores.putIfAbsent('David', () => 75);
  
  // Merge maps
  var defaults = {'theme': 'light', 'fontSize': 14};
  var userSettings = {'theme': 'dark'};
  var finalSettings = {...defaults, ...userSettings};
  print(finalSettings); // {theme: dark, fontSize: 14}
  
  // Iteration
  person.forEach((key, value) {
    print('$key: $value');
  });
  
  for (var entry in person.entries) {
    print('${entry.key}: ${entry.value}');
  }
  
  for (var key in person.keys) {
    print('$key: ${person[key]}');
  }
  
  // Transform
  var doubled = map2.map((key, value) => MapEntry(key, value * 2));
  print(doubled); // {a: 2, b: 4, c: 6}
  
  // Nested maps
  var users = {
    'user1': {'name': 'Alice', 'age': 30},
    'user2': {'name': 'Bob', 'age': 25},
  };
  
  print(users['user1']?['name']); // Alice
}
```

### Queues

```dart
import 'dart:collection';

void queuesDemo() {
  // Creating queues
  var queue = Queue<int>();
  queue.addAll([1, 2, 3]);
  
  // Add elements
  queue.addFirst(0);    // Add to front
  queue.addLast(4);     // Add to back
  print(queue);         // {0, 1, 2, 3, 4}
  
  // Remove elements
  var first = queue.removeFirst();  // 0
  var last = queue.removeLast();    // 4
  print(queue);                      // {1, 2, 3}
  
  // Peek
  print(queue.first);   // 1 (doesn't remove)
  print(queue.last);    // 3 (doesn't remove)
  
  // Queue from list
  var listQueue = Queue.from([1, 2, 3, 4, 5]);
  
  // FIFO behavior
  var fifo = Queue<String>();
  fifo.add('First');
  fifo.add('Second');
  fifo.add('Third');
  
  print(fifo.removeFirst()); // First
  print(fifo.removeFirst()); // Second
}
```

### Custom Collections

```dart
class Stack<T> {
  final List<T> _items = [];
  
  void push(T item) => _items.add(item);
  
  T? pop() => _items.isEmpty ? null : _items.removeLast();
  
  T? peek() => _items.isEmpty ? null : _items.last;
  
  bool get isEmpty => _items.isEmpty;
  
  int get length => _items.length;
  
  void clear() => _items.clear();
  
  @override
  String toString() => _items.toString();
}

class CircularBuffer<T> {
  final int capacity;
  final List<T?> _buffer;
  int _writeIndex = 0;
  int _size = 0;
  
  CircularBuffer(this.capacity) : _buffer = List<T?>.filled(capacity, null);
  
  void add(T item) {
    _buffer[_writeIndex] = item;
    _writeIndex = (_writeIndex + 1) % capacity;
    if (_size < capacity) _size++;
  }
  
  List<T> toList() {
    var result = <T>[];
    var readIndex = _size < capacity ? 0 : _writeIndex;
    
    for (var i = 0; i < _size; i++) {
      var item = _buffer[readIndex];
      if (item != null) result.add(item);
      readIndex = (readIndex + 1) % capacity;
    }
    
    return result;
  }
  
  int get length => _size;
  bool get isEmpty => _size == 0;
  bool get isFull => _size == capacity;
}

void customCollectionsDemo() {
  // Stack usage
  var stack = Stack<int>();
  stack.push(1);
  stack.push(2);
  stack.push(3);
  print(stack);         // [1, 2, 3]
  print(stack.pop());   // 3
  print(stack.peek());  // 2
  
  // Circular buffer usage
  var buffer = CircularBuffer<int>(3);
  buffer.add(1);
  buffer.add(2);
  buffer.add(3);
  print(buffer.toList()); // [1, 2, 3]
  
  buffer.add(4); // Overwrites 1
  print(buffer.toList()); // [2, 3, 4]
}
```

## 6. Object-Oriented Programming

### Classes and Objects

```dart
// Basic class
class Person {
  // Properties
  String name;
  int age;
  
  // Constructor
  Person(this.name, this.age);
  
  // Named constructor
  Person.guest() : this('Guest', 0);
  
  Person.fromJson(Map<String, dynamic> json)
      : name = json['name'],
        age = json['age'];
  
  // Methods
  void introduce() {
    print('Hi, I\'m $name and I\'m $age years old.');
  }
  
  // Getter
  bool get isAdult => age >= 18;
  
  // Setter
  set updateAge(int newAge) {
    if (newAge >= 0) age = newAge;
  }
  
  // Override toString
  @override
  String toString() => 'Person(name: $name, age: $age)';
}

// Class with private members
class BankAccount {
  String _accountNumber;
  double _balance = 0.0;
  
  BankAccount(this._accountNumber);
  
  // Public getter
  double get balance => _balance;
  
  String get accountNumber => _accountNumber;
  
  // Public methods
  void deposit(double amount) {
    if (amount > 0) {
      _balance += amount;
      _logTransaction('Deposit', amount);
    }
  }
  
  bool withdraw(double amount) {
    if (amount > 0 && amount <= _balance) {
      _balance -= amount;
      _logTransaction('Withdrawal', amount);
      return true;
    }
    return false;
  }
  
  // Private method
  void _logTransaction(String type, double amount) {
    print('$type: \$${amount.toStringAsFixed(2)}');
  }
}

void classesDemo() {
  // Create objects
  var person1 = Person('Alice', 30);
  person1.introduce();
  print(person1.isAdult);
  
  var person2 = Person.guest();
  print(person2);
  
  var person3 = Person.fromJson({'name': 'Bob', 'age': 25});
  
  // Bank account
  var account = BankAccount('123456');
  account.deposit(1000);
  account.withdraw(250);
  print('Balance: \$${account.balance}');
}
```

### Inheritance

```dart
// Base class
class Animal {
  String name;
  int age;
  
  Animal(this.name, this.age);
  
  void makeSound() {
    print('Some generic animal sound');
  }
  
  void eat() {
    print('$name is eating');
  }
}

// Derived class
class Dog extends Animal {
  String breed;
  
  Dog(String name, int age, this.breed) : super(name, age);
  
  @override
  void makeSound() {
    print('$name barks: Woof! Woof!');
  }
  
  void fetch() {
    print('$name is fetching the ball');
  }
}

class Cat extends Animal {
  bool isIndoor;
  
  Cat(String name, int age, this.isIndoor) : super(name, age);
  
  @override
  void makeSound() {
    print('$name meows: Meow!');
  }
  
  void scratch() {
    print('$name is scratching');
  }
}

// Multi-level inheritance
class Puppy extends Dog {
  Puppy(String name, String breed) : super(name, 0, breed);
  
  void play() {
    print('$name the puppy is playing');
  }
}

void inheritanceDemo() {
  var dog = Dog('Buddy', 5, 'Golden Retriever');
  dog.makeSound();  // Buddy barks: Woof! Woof!
  dog.eat();        // Buddy is eating
  dog.fetch();      // Buddy is fetching the ball
  
  var cat = Cat('Whiskers', 3, true);
  cat.makeSound();  // Whiskers meows: Meow!
  cat.scratch();    // Whiskers is scratching
  
  var puppy = Puppy('Max', 'Labrador');
  puppy.play();     // Max the puppy is playing
  puppy.makeSound(); // Max barks: Woof! Woof!
}
```

### Abstract Classes and Interfaces

```dart
// Abstract class
abstract class Shape {
  String name;
  
  Shape(this.name);
  
  // Abstract method
  double calculateArea();
  double calculatePerimeter();
  
  // Concrete method
  void display() {
    print('Shape: $name');
    print('Area: ${calculateArea()}');
    print('Perimeter: ${calculatePerimeter()}');
  }
}

class Rectangle extends Shape {
  double width;
  double height;
  
  Rectangle(this.width, this.height) : super('Rectangle');
  
  @override
  double calculateArea() => width * height;
  
  @override
  double calculatePerimeter() => 2 * (width + height);
}

class Circle extends Shape {
  double radius;
  
  Circle(this.radius) : super('Circle');
  
  @override
  double calculateArea() => 3.14159 * radius * radius;
  
  @override
  double calculatePerimeter() => 2 * 3.14159 * radius;
}

// Interface (using abstract class)
abstract class Drawable {
  void draw();
}

abstract class Movable {
  void move(double dx, double dy);
}

// Implementing multiple interfaces
class GameCharacter implements Drawable, Movable {
  String name;
  double x = 0;
  double y = 0;
  
  GameCharacter(this.name);
  
  @override
  void draw() {
    print('Drawing $name at ($x, $y)');
  }
  
  @override
  void move(double dx, double dy) {
    x += dx;
    y += dy;
    print('$name moved to ($x, $y)');
  }
}

void abstractDemo() {
  var rectangle = Rectangle(5, 3);
  rectangle.display();
  
  var circle = Circle(4);
  circle.display();
  
  var character = GameCharacter('Hero');
  character.draw();
  character.move(10, 20);
  character.draw();
}
```

### Mixins

```dart
// Mixin definitions
mixin Flying {
  void fly() {
    print('Flying in the sky');
  }
  
  void land() {
    print('Landing on the ground');
  }
}

mixin Swimming {
  void swim() {
    print('Swimming in water');
  }
}

mixin Walking {
  void walk() {
    print('Walking on land');
  }
}

// Base class
class Bird {
  String name;
  Bird(this.name);
  
  void eat() {
    print('$name is eating');
  }
}

// Using mixins
class Duck extends Bird with Swimming, Flying, Walking {
  Duck(String name) : super(name);
}

class Penguin extends Bird with Swimming, Walking {
  Penguin(String name) : super(name);
}

class Eagle extends Bird with Flying {
  Eagle(String name) : super(name);
}

// Mixin with constraints
mixin Aggressive on Bird {
  void attack() {
    print('$name is attacking!');
  }
}

class Hawk extends Bird with Flying, Aggressive {
  Hawk(String name) : super(name);
}

void mixinsDemo() {
  var duck = Duck('Donald');
  duck.eat();
  duck.swim();
  duck.fly();
  duck.walk();
  
  var penguin = Penguin('Pingu');
  penguin.swim();
  penguin.walk();
  // penguin.fly(); // Error: Penguin doesn't have Flying
  
  var hawk = Hawk('Hunter');
  hawk.fly();
  hawk.attack();
}
```

### Encapsulation and Access Control

```dart
// Library-private class (prefix with _)
class _InternalHelper {
  void process() {
    print('Internal processing');
  }
}

class User {
  // Private properties
  String _username;
  String _password;
  DateTime _lastLogin;
  
  // Public properties
  String email;
  
  User(this._username, this._password, this.email)
      : _lastLogin = DateTime.now();
  
  // Public getters
  String get username => _username;
  DateTime get lastLogin => _lastLogin;
  
  // Controlled setter
  set username(String value) {
    if (value.length >= 3) {
      _username = value;
    }
  }
  
  // Method with validation
  bool changePassword(String oldPassword, String newPassword) {
    if (_password == oldPassword && newPassword.length >= 8) {
      _password = newPassword;
      return true;
    }
    return false;
  }
  
  // Public method
  void login() {
    _lastLogin = DateTime.now();
    print('$_username logged in');
  }
  
  // Private method
  void _validateSession() {
    // Internal validation logic
  }
}

class SecureVault {
  final Map<String, String> _secrets = {};
  
  void store(String key, String secret) {
    _secrets[key] = _encrypt(secret);
  }
  
  String? retrieve(String key) {
    var encrypted = _secrets[key];
    return encrypted != null ? _decrypt(encrypted) : null;
  }
  
  String _encrypt(String data) {
    // Simple encryption for demo
    return data.split('').reversed.join();
  }
  
  String _decrypt(String data) {
    return data.split('').reversed.join();
  }
}

void encapsulationDemo() {
  var user = User('alice', 'password123', 'alice@example.com');
  print(user.username);
  user.login();
  user.changePassword('password123', 'newpassword456');
  
  var vault = SecureVault();
  vault.store('apiKey', 'secret123');
  print(vault.retrieve('apiKey'));
}
```

### Static Members and Factory Constructors

```dart
class MathUtils {
  // Static constants
  static const double pi = 3.14159;
  static const double e = 2.71828;
  
  // Static methods
  static double square(double x) => x * x;
  
  static double cube(double x) => x * x * x;
  
  static int factorial(int n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
  }
}

class Database {
  static final Database _instance = Database._internal();
  
  // Private constructor
  Database._internal();
  
  // Factory constructor (Singleton pattern)
  factory Database() {
    return _instance;
  }
  
  void query(String sql) {
    print('Executing: $sql');
  }
}

class Color {
  final int red;
  final int green;
  final int blue;
  
  Color(this.red, this.green, this.blue);
  
  // Named constructors
  Color.red() : this(255, 0, 0);
  Color.green() : this(0, 255, 0);
  Color.blue() : this(0, 0, 255);
  
  // Factory constructor
  factory Color.fromHex(String hex) {
    hex = hex.replaceAll('#', '');
    int value = int.parse(hex, radix: 16);
    int r = (value >> 16) & 0xFF;
    int g = (value >> 8) & 0xFF;
    int b = value & 0xFF;
    return Color(r, g, b);
  }
  
  @override
  String toString() => 'Color(R:$red, G:$green, B:$blue)';
}

void staticDemo() {
  // Static members
  print(MathUtils.pi);
  print(MathUtils.square(5));
  print(MathUtils.factorial(5));
  
  // Singleton
  var db1 = Database();
  var db2 = Database();
  print(identical(db1, db2)); // true (same instance)
  
  // Factory constructors
  var red = Color.red();
  var custom = Color.fromHex('#FF5733');
  print(red);
  print(custom);
}
```

### Operator Overloading

```dart
class Vector {
  final double x;
  final double y;
  
  Vector(this.x, this.y);
  
  // Overload + operator
  Vector operator +(Vector other) {
    return Vector(x + other.x, y + other.y);
  }
  
  // Overload - operator
  Vector operator -(Vector other) {
    return Vector(x - other.x, y - other.y);
  }
  
  // Overload * operator (scalar multiplication)
  Vector operator *(double scalar) {
    return Vector(x * scalar, y * scalar);
  }
  
  // Overload / operator
  Vector operator /(double scalar) {
    return Vector(x / scalar, y / scalar);
  }
  
  // Overload == operator
  @override
  bool operator ==(Object other) {
    if (other is! Vector) return false;
    return x == other.x && y == other.y;
  }
  
  @override
  int get hashCode => Object.hash(x, y);
  
  // Overload [] operator (getter)
  double operator [](int index) {
    if (index == 0) return x;
    if (index == 1) return y;
    throw RangeError('Index out of range: $index');
  }
  
  double get magnitude => (x * x + y * y).abs();
  
  @override
  String toString() => 'Vector($x, $y)';
}

class Matrix {
  final List<List<double>> data;
  
  Matrix(this.data);
  
  int get rows => data.length;
  int get cols => data[0].length;
  
  // Overload [] for access
  List<double> operator [](int index) => data[index];
  
  // Matrix multiplication
  Matrix operator *(Matrix other) {
    if (cols != other.rows) {
      throw ArgumentError('Invalid dimensions for multiplication');
    }
    
    var result = List.generate(
      rows,
      (i) => List.generate(other.cols, (j) {
        double sum = 0;
        for (var k = 0; k < cols; k++) {
          sum += data[i][k] * other.data[k][j];
        }
        return sum;
      }),
    );
    
    return Matrix(result);
  }
  
  @override
  String toString() {
    return data.map((row) => row.toString()).join('\n');
  }
}

void operatorOverloadingDemo() {
  var v1 = Vector(3, 4);
  var v2 = Vector(1, 2);
  
  var sum = v1 + v2;
  var diff = v1 - v2;
  var scaled = v1 * 2;
  
  print('v1 + v2 = $sum');
  print('v1 - v2 = $diff');
  print('v1 * 2 = $scaled');
  print('v1[0] = ${v1[0]}, v1[1] = ${v1[1]}');
  print('v1 == v2: ${v1 == v2}');
  
  var m1 = Matrix([[1, 2], [3, 4]]);
  var m2 = Matrix([[5, 6], [7, 8]]);
  var product = m1 * m2;
  print('Matrix product:\n$product');
}
```

## 7. Functional Programming Concepts

### First-Class Functions

```dart
// Function types
typedef BinaryOperation = int Function(int, int);
typedef Predicate<T> = bool Function(T);
typedef Mapper<T, R> = R Function(T);

// Functions as values
int add(int a, int b) => a + b;
int subtract(int a, int b) => a - b;
int multiply(int a, int b) => a * b;

void firstClassFunctionsDemo() {
  // Store function in variable
  BinaryOperation operation = add;
  print(operation(5, 3)); // 8
  
  operation = multiply;
  print(operation(5, 3)); // 15
  
  // List of functions
  var operations = [add, subtract, multiply];
  for (var op in operations) {
    print(op(10, 5));
  }
  
  // Map of functions
  var calculator = <String, BinaryOperation>{
    'add': add,
    'subtract': subtract,
    'multiply': multiply,
  };
  
  print(calculator['add']!(7, 3)); // 10
}
```

### Higher-Order Functions

```dart
// Function that takes function as parameter
T apply<T>(T value, T Function(T) transformer) {
  return transformer(value);
}

// Function that returns function
Function makeMultiplier(int factor) {
  return (int value) => value * factor;
}

// Compose functions
Function compose(Function f, Function g) {
  return (x) => f(g(x));
}

void higherOrderFunctionsDemo() {
  // Pass function as argument
  var result = apply(5, (x) => x * x);
  print(result); // 25
  
  result = apply(5, (x) => x + 10);
  print(result); // 15
  
  // Return function
  var times2 = makeMultiplier(2);
  var times10 = makeMultiplier(10);
  
  print(times2(5));  // 10
  print(times10(5)); // 50
  
  // Function composition
  var double = (int x) => x * 2;
  var addFive = (int x) => x + 5;
  var doubleThenAddFive = compose(addFive, double);
  
  print(doubleThenAddFive(3)); // (3 * 2) + 5 = 11
}
```

### Map, Filter, Reduce

```dart
void functionalOperationsDemo() {
  var numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  
  // Map - transform each element
  var squared = numbers.map((n) => n * n).toList();
  print(squared); // [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
  
  var strings = numbers.map((n) => 'Number: $n').toList();
  print(strings);
  
  // Filter (where) - select elements
  var evens = numbers.where((n) => n % 2 == 0).toList();
  print(evens); // [2, 4, 6, 8, 10]
  
  var greaterThanFive = numbers.where((n) => n > 5).toList();
  print(greaterThanFive); // [6, 7, 8, 9, 10]
  
  // Reduce - combine elements
  var sum = numbers.reduce((a, b) => a + b);
  print(sum); // 55
  
  var product = numbers.reduce((a, b) => a * b);
  print(product); // 3628800
  
  // Fold - reduce with initial value
  var sumFrom100 = numbers.fold(100, (prev, element) => prev + element);
  print(sumFrom100); // 155
  
  // Chain operations
  var result = numbers
      .where((n) => n % 2 == 0)
      .map((n) => n * n)
      .reduce((a, b) => a + b);
  print(result); // 220 (2^2 + 4^2 + 6^2 + 8^2 + 10^2)
  
  // Any and Every
  print(numbers.any((n) => n > 5));    // true
  print(numbers.every((n) => n > 0));  // true
  print(numbers.every((n) => n > 5));  // false
  
  // TakeWhile and SkipWhile
  var takeWhile = numbers.takeWhile((n) => n < 5).toList();
  print(takeWhile); // [1, 2, 3, 4]
  
  var skipWhile = numbers.skipWhile((n) => n < 5).toList();
  print(skipWhile); // [5, 6, 7, 8, 9, 10]
  
  // Expand (flatMap)
  var expanded = numbers.take(3).expand((n) => [n, n * 10]).toList();
  print(expanded); // [1, 10, 2, 20, 3, 30]
}
```

### Immutability and Pure Functions

```dart
// Pure function - same input always gives same output, no side effects
int pureAdd(int a, int b) => a + b;

int pureFactorial(int n) {
  if (n <= 1) return 1;
  return n * pureFactorial(n - 1);
}

// Immutable class
class ImmutablePoint {
  final double x;
  final double y;
  
  const ImmutablePoint(this.x, this.y);
  
  // Returns new instance instead of modifying
  ImmutablePoint move(double dx, double dy) {
    return ImmutablePoint(x + dx, y + dy);
  }
  
  ImmutablePoint scale(double factor) {
    return ImmutablePoint(x * factor, y * factor);
  }
  
  @override
  String toString() => 'Point($x, $y)';
}

// Immutable collection operations
List<int> immutableAdd(List<int> list, int value) {
  return [...list, value];
}

List<int> immutableRemove(List<int> list, int value) {
  return list.where((item) => item != value).toList();
}

List<int> immutableUpdate(List<int> list, int index, int value) {
  return List.generate(list.length, (i) => i == index ? value : list[i]);
}

void immutabilityDemo() {
  // Pure functions
  print(pureAdd(5, 3));        // Always 8
  print(pureFactorial(5));     // Always 120
  
  // Immutable objects
  var point = ImmutablePoint(3, 4);
  var movedPoint = point.move(2, 1);
  var scaledPoint = point.scale(2);
  
  print('Original: $point');      // Point(3, 4)
  print('Moved: $movedPoint');    // Point(5, 5)
  print('Scaled: $scaledPoint');  // Point(6, 8)
  
  // Immutable list operations
  var original = [1, 2, 3];
  var withFour = immutableAdd(original, 4);
  var withoutTwo = immutableRemove(original, 2);
  var updated = immutableUpdate(original, 1, 10);
  
  print('Original: $original');      // [1, 2, 3]
  print('With 4: $withFour');        // [1, 2, 3, 4]
  print('Without 2: $withoutTwo');   // [1, 3]
  print('Updated: $updated');        // [1, 10, 3]
}
```

### Currying and Partial Application

```dart
// Currying - transform function with multiple args to sequence of functions
Function curry2(Function f) {
  return (a) => (b) => Function.apply(f, [a, b]);
}

Function curry3(Function f) {
  return (a) => (b) => (c) => Function.apply(f, [a, b, c]);
}

// Partial application
Function partial(Function f, List args) {
  return (List moreArgs) => Function.apply(f, [...args, ...moreArgs]);
}

void curryingDemo() {
  // Manual currying
  int add(int a, int b) => a + b;
  var curriedAdd = (int a) => (int b) => add(a, b);
  
  var add5 = curriedAdd(5);
  print(add5(3));  // 8
  print(add5(10)); // 15
  
  // Multi-parameter currying
  int addThree(int a, int b, int c) => a + b + c;
  var curriedAddThree = (int a) => (int b) => (int c) => addThree(a, b, c);
  
  var add10And = curriedAddThree(10);
  var add10And20 = add10And(20);
  print(add10And20(5)); // 35
  
  // Practical example
  String greet(String greeting, String name) => '$greeting, $name!';
  var curriedGreet = (String greeting) => (String name) => greet(greeting, name);
  
  var sayHello = curriedGreet('Hello');
  var sayHi = curriedGreet('Hi');
  
  print(sayHello('Alice'));  // Hello, Alice!
  print(sayHi('Bob'));       // Hi, Bob!
}
```

### Lazy Evaluation

```dart
// Generator for lazy sequences
Iterable<int> lazyRange(int start, int end) sync* {
  for (var i = start; i < end; i++) {
    yield i;
  }
}

Iterable<int> lazyFibonacci() sync* {
  var a = 0, b = 1;
  while (true) {
    yield a;
    var temp = a;
    a = b;
    b = temp + b;
  }
}

// Lazy evaluation with streams
Stream<int> lazyNumbers(int max) async* {
  for (var i = 0; i < max; i++) {
    await Future.delayed(Duration(milliseconds: 100));
    yield i;
  }
}

void lazyEvaluationDemo() {
  // Lazy sequences
  var range = lazyRange(0, 1000000); // Doesn't compute yet
  var first10 = range.take(10).toList(); // Only computes first 10
  print(first10);
  
  // Infinite lazy sequence
  var fibonacci = lazyFibonacci();
  var firstFib10 = fibonacci.take(10).toList();
  print(firstFib10);
  
  // Lazy filtering and mapping
  var evenSquares = lazyRange(1, 100)
      .where((n) => n % 2 == 0)
      .map((n) => n * n)
      .take(5)
      .toList();
  print(evenSquares);
  
  // Chained lazy operations
  var result = lazyRange(1, 1000)
      .where((n) => n % 3 == 0)
      .map((n) => n * 2)
      .skip(5)
      .take(10)
      .toList();
  print(result);
}
```

## 8. Memory Management

### Value Types vs Reference Types

```dart
void memoryBasicsDemo() {
  // Value types (stored on stack or as immediate values)
  int a = 10;
  int b = a;
  b = 20;
  print('a = $a, b = $b'); // a = 10, b = 20 (independent copies)
  
  double x = 3.14;
  double y = x;
  y = 2.71;
  print('x = $x, y = $y'); // x = 3.14, y = 2.71
  
  // Reference types (stored on heap)
  var list1 = [1, 2, 3];
  var list2 = list1; // Reference copy
  list2.add(4);
  print('list1 = $list1'); // [1, 2, 3, 4] (both point to same object)
  print('list2 = $list2'); // [1, 2, 3, 4]
  
  // Creating actual copy
  var list3 = List.from(list1);
  list3.add(5);
  print('list1 = $list1'); // [1, 2, 3, 4]
  print('list3 = $list3'); // [1, 2, 3, 4, 5]
}
```

### Garbage Collection

```dart
class Resource {
  final String name;
  
  Resource(this.name) {
    print('$name created');
  }
  
  void use() {
    print('Using $name');
  }
}

void garbageCollectionDemo() {
  // Object created and stored in variable
  var resource = Resource('Resource1');
  resource.use();
  
  // Object eligible for GC when no references remain
  resource = Resource('Resource2'); // Resource1 now eligible for GC
  resource.use();
  
  // Objects in collections
  var resources = <Resource>[];
  resources.add(Resource('Resource3'));
  resources.add(Resource('Resource4'));
  
  resources.clear(); // Resource3 and Resource4 eligible for GC
  
  // Circular references are handled by Dart's GC
  var node1 = TreeNode('Node1');
  var node2 = TreeNode('Node2');
  node1.child = node2;
  node2.child = node1; // Circular reference
  
  // Both become eligible for GC when no external references exist
}

class TreeNode {
  String name;
  TreeNode? child;
  
  TreeNode(this.name);
}
```

### Memory Optimization

```dart
// Const constructors for compile-time constants
class ImmutableConfig {
  final String apiUrl;
  final int timeout;
  
  const ImmutableConfig(this.apiUrl, this.timeout);
}

// Reusing const instances
void constOptimizationDemo() {
  // These share the same memory location
  const config1 = ImmutableConfig('https://api.example.com', 30);
  const config2 = ImmutableConfig('https://api.example.com', 30);
  
  print(identical(config1, config2)); // true (same object in memory)
  
  // Non-const instances are different
  var config3 = ImmutableConfig('https://api.example.com', 30);
  var config4 = ImmutableConfig('https://api.example.com', 30);
  
  print(identical(config3, config4)); // false (different objects)
}

// String interning (automatic in Dart)
void stringInterningDemo() {
  var str1 = 'Hello';
  var str2 = 'Hello';
  
  print(identical(str1, str2)); // true (string literals are interned)
  
  var str3 = 'Hello' + '';
  print(identical(str1, str3)); // false (computed string)
}

// Lazy initialization
class LazyResource {
  late final ExpensiveObject _resource;
  
  ExpensiveObject get resource {
    // Only created when first accessed
    return _resource;
  }
  
  void initialize() {
    _resource = ExpensiveObject();
  }
}

class ExpensiveObject {
  ExpensiveObject() {
    print('Expensive object created');
  }
}

// Object pooling
class ObjectPool<T> {
  final List<T> _pool = [];
  final T Function() _creator;
  
  ObjectPool(this._creator);
  
  T acquire() {
    if (_pool.isNotEmpty) {
      return _pool.removeLast();
    }
    return _creator();
  }
  
  void release(T object) {
    _pool.add(object);
  }
}

void poolingDemo() {
  var pool = ObjectPool<List<int>>(() => <int>[]);
  
  // Acquire from pool
  var list1 = pool.acquire();
  list1.addAll([1, 2, 3]);
  print(list1);
  
  // Return to pool
  list1.clear();
  pool.release(list1);
  
  // Reuse same object
  var list2 = pool.acquire();
  print(identical(list1, list2)); // true if pool is used correctly
}
```

### WeakReference

```dart
class Cache {
  final Map<String, WeakReference<LargeObject>> _cache = {};
  
  void store(String key, LargeObject object) {
    _cache[key] = WeakReference(object);
  }
  
  LargeObject? retrieve(String key) {
    var weakRef = _cache[key];
    return weakRef?.target; // May return null if GC collected it
  }
  
  void cleanup() {
    _cache.removeWhere((key, weakRef) => weakRef.target == null);
  }
}

class LargeObject {
  final List<int> data;
  final String id;
  
  LargeObject(this.id) : data = List.filled(1000000, 0) {
    print('Created large object: $id');
  }
}

void weakReferenceDemo() {
  var cache = Cache();
  
  // Strong reference
  var obj = LargeObject('obj1');
  cache.store('key1', obj);
  
  print(cache.retrieve('key1')); // Available
  
  // Remove strong reference
  obj = LargeObject('obj2');
  // obj1 may be garbage collected
  
  cache.cleanup(); // Remove dead weak references
}
```

### Memory Profiling Tips

```dart
void memoryProfilingDemo() {
  // Avoid creating unnecessary objects in loops
  // BAD:
  for (var i = 0; i < 1000; i++) {
    var temp = <int>[]; // Creates 1000 lists
    temp.add(i);
  }
  
  // GOOD:
  var result = <int>[];
  for (var i = 0; i < 1000; i++) {
    result.add(i);
  }
  
  // Use const for immutable values
  const config = {'timeout': 30, 'retries': 3};
  
  // Use final for variables that won't change
  final timestamp = DateTime.now();
  
  // Avoid holding references longer than necessary
  void processLargeData() {
    var data = List.filled(1000000, 0);
    // Process data
    print(data.length);
    // data is eligible for GC after function returns
  }
  
  processLargeData();
  
  // Clear collections when done
  var cache = <String, Object>{};
  // ... use cache ...
  cache.clear(); // Free memory
}
```

## 9. Standard Library

### Collections Library

```dart
import 'dart:collection';

void collectionsLibraryDemo() {
  // LinkedList
  var linkedList = LinkedList<EntryItem>();
  linkedList.add(EntryItem(1));
  linkedList.add(EntryItem(2));
  linkedList.add(EntryItem(3));
  
  for (var entry in linkedList) {
    print(entry.value);
  }
  
  // HashMap
  var hashMap = HashMap<String, int>();
  hashMap['one'] = 1;
  hashMap['two'] = 2;
  hashMap['three'] = 3;
  
  // LinkedHashMap (maintains insertion order)
  var linkedHashMap = LinkedHashMap<String, int>();
  linkedHashMap['a'] = 1;
  linkedHashMap['c'] = 3;
  linkedHashMap['b'] = 2;
  print(linkedHashMap.keys); // (a, c, b)
  
  // SplayTreeMap (sorted keys)
  var treeMap = SplayTreeMap<int, String>();
  treeMap[3] = 'three';
  treeMap[1] = 'one';
  treeMap[2] = 'two';
  print(treeMap.keys); // (1, 2, 3)
  
  // HashSet
  var hashSet = HashSet<int>();
  hashSet.addAll([1, 2, 3, 2, 1]);
  print(hashSet); // {1, 2, 3}
  
  // LinkedHashSet (maintains insertion order)
  var linkedHashSet = LinkedHashSet<String>();
  linkedHashSet.addAll(['banana', 'apple', 'cherry']);
  print(linkedHashSet); // {banana, apple, cherry}
  
  // SplayTreeSet (sorted)
  var treeSet = SplayTreeSet<int>();
  treeSet.addAll([3, 1, 4, 1, 5, 9, 2, 6]);
  print(treeSet); // {1, 2, 3, 4, 5, 6, 9}
  
  // Queue
  var queue = Queue<String>();
  queue.addAll(['first', 'second', 'third']);
  print(queue.removeFirst()); // first
  print(queue.removeLast());  // third
}

class EntryItem extends LinkedListEntry<EntryItem> {
  final int value;
  EntryItem(this.value);
}
```

### Math Library

```dart
import 'dart:math';

void mathLibraryDemo() {
  // Constants
  print('Pi: ${pi}');
  print('E: ${e}');
  
  // Basic operations
  print('Max: ${max(10, 20)}');
  print('Min: ${min(10, 20)}');
  
  // Power and roots
  print('2^3 = ${pow(2, 3)}');
  print('sqrt(16) = ${sqrt(16)}');
  
  // Exponential and logarithm
  print('e^2 = ${exp(2)}');
  print('ln(10) = ${log(10)}');
  
  // Trigonometry
  print('sin(pi/2) = ${sin(pi / 2)}');
  print('cos(0) = ${cos(0)}');
  print('tan(pi/4) = ${tan(pi / 4)}');
  
  // Inverse trig
  print('asin(1) = ${asin(1)}');
  print('acos(1) = ${acos(1)}');
  print('atan(1) = ${atan(1)}');
  print('atan2(1, 1) = ${atan2(1, 1)}');
  
  // Rounding
  print('ceil(4.2) = ${4.2.ceil()}');
  print('floor(4.8) = ${4.8.floor()}');
  print('round(4.5) = ${4.5.round()}');
  print('truncate(4.9) = ${4.9.truncate()}');
  
  // Random numbers
  var random = Random();
  print('Random int: ${random.nextInt(100)}');
  print('Random double: ${random.nextDouble()}');
  print('Random bool: ${random.nextBool()}');
  
  // Random with seed (reproducible)
  var seededRandom = Random(42);
  print('Seeded: ${seededRandom.nextInt(100)}');
  
  // Point and Rectangle
  var point = Point(3, 4);
  print('Distance from origin: ${point.distanceTo(Point(0, 0))}');
  
  var rect = Rectangle(0, 0, 100, 50);
  print('Area: ${rect.width * rect.height}');
  print('Contains point: ${rect.containsPoint(Point(25, 25))}');
}
```

### DateTime and Duration

```dart
void dateTimeDemo() {
  // Current date and time
  var now = DateTime.now();
  print('Now: $now');
  
  // Creating specific date
  var date = DateTime(2024, 1, 15, 14, 30, 45);
  print('Specific: $date');
  
  // UTC
  var utc = DateTime.utc(2024, 1, 15, 12, 0, 0);
  print('UTC: $utc');
  
  // Parse from string
  var parsed = DateTime.parse('2024-01-15 14:30:00');
  print('Parsed: $parsed');
  
  // Components
  print('Year: ${now.year}');
  print('Month: ${now.month}');
  print('Day: ${now.day}');
  print('Hour: ${now.hour}');
  print('Minute: ${now.minute}');
  print('Second: ${now.second}');
  print('Weekday: ${now.weekday}'); // 1 = Monday, 7 = Sunday
  
  // Comparisons
  var future = now.add(Duration(days: 7));
  print('Is before: ${now.isBefore(future)}');
  print('Is after: ${now.isAfter(future)}');
  
  // Difference
  var diff = future.difference(now);
  print('Difference: ${diff.inDays} days');
  
  // Duration
  var duration = Duration(
    days: 1,
    hours: 2,
    minutes: 30,
    seconds: 45,
    milliseconds: 500,
  );
  
  print('Total seconds: ${duration.inSeconds}');
  print('Total minutes: ${duration.inMinutes}');
  print('Total hours: ${duration.inHours}');
  
  // Add/Subtract duration
  var tomorrow = now.add(Duration(days: 1));
  var yesterday = now.subtract(Duration(days: 1));
  
  print('Tomorrow: $tomorrow');
  print('Yesterday: $yesterday');
  
  // Format (requires intl package in production)
  print('ISO 8601: ${now.toIso8601String()}');
  print('UTC: ${now.toUtc()}');
  print('Local: ${now.toLocal()}');
}
```

### Async Library

```dart
import 'dart:async';

void asyncLibraryDemo() async {
  // Future.delayed
  await Future.delayed(Duration(seconds: 1), () {
    print('After 1 second');
  });
  
  // Future.value
  var immediateFuture = Future.value(42);
  print(await immediateFuture);
  
  // Future.error
  try {
    await Future.error('Error occurred');
  } catch (e) {
    print('Caught: $e');
  }
  
  // Future.wait (parallel execution)
  var futures = [
    Future.delayed(Duration(seconds: 1), () => 1),
    Future.delayed(Duration(seconds: 1), () => 2),
    Future.delayed(Duration(seconds: 1), () => 3),
  ];
  
  var results = await Future.wait(futures);
  print('Results: $results');
  
  // Future.any (first to complete)
  var first = await Future.any([
    Future.delayed(Duration(seconds: 2), () => 'slow'),
    Future.delayed(Duration(seconds: 1), () => 'fast'),
  ]);
  print('First: $first');
  
  // Completer (manual Future control)
  var completer = Completer<String>();
  
  Future.delayed(Duration(seconds: 1), () {
    completer.complete('Completed!');
  });
  
  print(await completer.future);
  
  // Stream creation
  var stream = Stream.periodic(
    Duration(milliseconds: 500),
    (count) => count,
  ).take(5);
  
  await for (var value in stream) {
    print('Stream value: $value');
  }
  
  // StreamController
  var controller = StreamController<int>();
  
  controller.stream.listen((value) {
    print('Received: $value');
  });
  
  controller.add(1);
  controller.add(2);
  controller.add(3);
  controller.close();
  
  await Future.delayed(Duration(milliseconds: 100));
}
```

### Convert Library (JSON, Encoding)

```dart
import 'dart:convert';

void convertLibraryDemo() {
  // JSON encoding
  var data = {
    'name': 'Alice',
    'age': 30,
    'hobbies': ['reading', 'coding', 'gaming'],
    'address': {
      'city': 'New York',
      'zip': '10001',
    },
  };
  
  var jsonString = jsonEncode(data);
  print('JSON: $jsonString');
  
  // JSON decoding
  var decoded = jsonDecode(jsonString);
  print('Name: ${decoded['name']}');
  print('City: ${decoded['address']['city']}');
  
  // Pretty print JSON
  var encoder = JsonEncoder.withIndent('  ');
  print(encoder.convert(data));
  
  // Base64 encoding
  var bytes = utf8.encode('Hello, World!');
  var base64String = base64Encode(bytes);
  print('Base64: $base64String');
  
  // Base64 decoding
  var decodedBytes = base64Decode(base64String);
  var decodedString = utf8.decode(decodedBytes);
  print('Decoded: $decodedString');
  
  // URL encoding
  var url = 'Hello World & Special Characters!';
  var encoded = Uri.encodeComponent(url);
  print('URL encoded: $encoded');
  
  var decodedUrl = Uri.decodeComponent(encoded);
  print('URL decoded: $decodedUrl');
  
  // UTF-8 encoding/decoding
  var text = 'Hello, 世界! 🌍';
  var utf8Bytes = utf8.encode(text);
  print('UTF-8 bytes: $utf8Bytes');
  
  var utf8Text = utf8.decode(utf8Bytes);
  print('UTF-8 text: $utf8Text');
  
  // Latin1 encoding
  var latin1Text = 'Hello';
  var latin1Bytes = latin1.encode(latin1Text);
  print('Latin1 bytes: $latin1Bytes');
  
  // ASCII encoding
  var asciiText = 'ABC123';
  var asciiBytes = ascii.encode(asciiText);
  print('ASCII bytes: $asciiBytes');
}
```

### IO Library

```dart
import 'dart:io';

void ioLibraryDemo() async {
  // File operations
  var file = File('test.txt');
  
  // Write to file
  await file.writeAsString('Hello, Dart!');
  
  // Read from file
  var contents = await file.readAsString();
  print('File contents: $contents');
  
  // Append to file
  await file.writeAsString('\nNew line', mode: FileMode.append);
  
  // Read as lines
  var lines = await file.readAsLines();
  print('Lines: $lines');
  
  // Read as bytes
  var bytes = await file.readAsBytes();
  print('Bytes: ${bytes.length}');
  
  // File info
  print('Exists: ${await file.exists()}');
  print('Path: ${file.path}');
  print('Absolute path: ${file.absolute.path}');
  
  var stat = await file.stat();
  print('Size: ${stat.size} bytes');
  print('Modified: ${stat.modified}');
  
  // Delete file
  if (await file.exists()) {
    await file.delete();
  }
  
  // Directory operations
  var dir = Directory('test_dir');
  
  if (!await dir.exists()) {
    await dir.create();
  }
  
  // List directory contents
  await for (var entity in dir.list()) {
    print(entity.path);
  }
  
  // Delete directory
  if (await dir.exists()) {
    await dir.delete(recursive: true);
  }
  
  // Path operations
  print('Current directory: ${Directory.current.path}');
  print('Separator: ${Platform.pathSeparator}');
  
  // Environment variables
  print('PATH: ${Platform.environment['PATH']}');
  
  // Platform information
  print('OS: ${Platform.operatingSystem}');
  print('Number of processors: ${Platform.numberOfProcessors}');
}
```

## 10. Tooling and Ecosystem

### Dart SDK and Tools

```dart
// pubspec.yaml example
/*
name: my_dart_app
description: A sample Dart application
version: 1.0.0

environment:
  sdk: '>=3.0.0 <4.0.0'

dependencies:
  http: ^1.1.0
  intl: ^0.18.0

dev_dependencies:
  test: ^1.24.0
  lints: ^2.1.0
*/
```

### Package Management

```bash
# Create new project
dart create my_app
dart create -t console my_console_app
dart create -t package my_package

# Get dependencies
dart pub get

# Update dependencies
dart pub upgrade

# Add dependency
dart pub add http
dart pub add --dev test

# Remove dependency
dart pub remove http

# Publish package
dart pub publish

# Run executable
dart pub global activate <package>
dart pub global run <package>

# Show outdated dependencies
dart pub outdated

# Dependency tree
dart pub deps
```

### Testing

```dart
import 'package:test/test.dart';

// Calculator class for testing
class Calculator {
  int add(int a, int b) => a + b;
  int subtract(int a, int b) => a - b;
  int multiply(int a, int b) => a * b;
  double divide(int a, int b) {
    if (b == 0) throw ArgumentError('Cannot divide by zero');
    return a / b;
  }
}

void main() {
  group('Calculator', () {
    late Calculator calculator;
    
    setUp(() {
      calculator = Calculator();
    });
    
    test('add returns sum of two numbers', () {
      expect(calculator.add(2, 3), equals(5));
      expect(calculator.add(-1, 1), equals(0));
    });
    
    test('subtract returns difference', () {
      expect(calculator.subtract(5, 3), equals(2));
      expect(calculator.subtract(3, 5), equals(-2));
    });
    
    test('multiply returns product', () {
      expect(calculator.multiply(3, 4), equals(12));
      expect(calculator.multiply(-2, 3), equals(-6));
    });
    
    test('divide returns quotient', () {
      expect(calculator.divide(10, 2), equals(5.0));
      expect(calculator.divide(7, 2), equals(3.5));
    });
    
    test('divide by zero throws error', () {
      expect(
        () => calculator.divide(10, 0),
        throwsArgumentError,
      );
    });
  });
  
  group('Matchers', () {
    test('equality matchers', () {
      expect(5, equals(5));
      expect('hello', equals('hello'));
      expect([1, 2, 3], equals([1, 2, 3]));
    });
    
    test('type matchers', () {
      expect(42, isA<int>());
      expect('text', isA<String>());
      expect([1, 2], isA<List<int>>());
    });
    
    test('numeric matchers', () {
      expect(5, greaterThan(3));
      expect(3, lessThan(5));
      expect(3, greaterThanOrEqualTo(3));
      expect(5, inInclusiveRange(1, 10));
      expect(3.14, closeTo(3.1, 0.1));
    });
    
    test('collection matchers', () {
      expect([1, 2, 3], contains(2));
      expect([1, 2, 3], containsAll([1, 3]));
      expect([1, 2, 3], hasLength(3));
      expect([1, 2, 3], isEmpty isFalse);
    });
    
    test('string matchers', () {
      expect('hello world', contains('world'));
      expect('hello', startsWith('hel'));
      expect('world', endsWith('rld'));
      expect('test123', matches(r'test\d+'));
    });
  });
  
  group('Async tests', () {
    test('future completes with value', () async {
      var future = Future.delayed(
        Duration(milliseconds: 100),
        () => 'done',
      );
      
      expect(await future, equals('done'));
    });
    
    test('future throws error', () {
      var future = Future.error('error');
      expect(future, throwsA(isA<String>()));
    });
    
    test('stream emits values', () async {
      var stream = Stream.fromIterable([1, 2, 3]);
      expect(stream, emitsInOrder([1, 2, 3]));
    });
  });
}
```

### Linting and Analysis

```yaml
# analysis_options.yaml
include: package:lints/recommended.yaml

analyzer:
  exclude:
    - "**/*.g.dart"
    - "**/*.freezed.dart"
  
  strong-mode:
    implicit-casts: false
    implicit-dynamic: false

linter:
  rules:
    - always_declare_return_types
    - always_put_required_named_parameters_first
    - avoid_print
    - avoid_redundant_argument_values
    - avoid_returning_null_for_void
    - prefer_const_constructors
    - prefer_final_fields
    - prefer_final_locals
    - prefer_single_quotes
    - sort_constructors_first
    - unnecessary_await_in_return
```

```bash
# Run analyzer
dart analyze

# Fix auto-fixable issues
dart fix --apply

# Format code
dart format .
dart format lib/

# Check formatting without changes
dart format --output=none --set-exit-if-changed .
```

### Documentation

```dart
/// A calculator class that performs basic arithmetic operations.
///
/// This class provides methods for addition, subtraction, multiplication,
/// and division. All operations work with integer inputs.
///
/// Example usage:
/// ```dart
/// var calc = Calculator();
/// print(calc.add(5, 3)); // 8
/// ```
class Calculator {
  /// Adds two integers and returns their sum.
  ///
  /// Parameters:
  ///   - [a]: First integer
  ///   - [b]: Second integer
  ///
  /// Returns the sum of [a] and [b].
  ///
  /// Example:
  /// ```dart
  /// var result = calculator.add(2, 3);
  /// print(result); // 5
  /// ```
  int add(int a, int b) => a + b;
  
  /// Divides [a] by [b] and returns the result.
  ///
  /// Throws [ArgumentError] if [b] is zero.
  double divide(int a, int b) {
    if (b == 0) {
      throw ArgumentError('Cannot divide by zero');
    }
    return a / b;
  }
}

// Generate documentation
// dart doc
// This creates documentation in doc/api/ directory
```

### Build and Compilation

```bash
# Run Dart file
dart run bin/main.dart
dart run lib/app.dart

# Compile to executable
dart compile exe bin/main.dart -o bin/app
dart compile exe bin/main.dart -o bin/app --target-os=windows

# Compile to JavaScript
dart compile js lib/app.dart -o build/app.js

# Compile to kernel
dart compile kernel bin/main.dart -o bin/app.dill

# AOT snapshot
dart compile aot-snapshot bin/main.dart

# JIT snapshot
dart compile jit-snapshot bin/main.dart

# Run with profiling
dart --observe run bin/main.dart
```

## 11. Best Practices

### Code Style

```dart
// Good naming conventions
class UserAccount { }           // Classes: PascalCase
void calculateTotal() { }       // Functions: camelCase
const maxRetries = 3;           // Constants: camelCase
final apiKey = 'key';          // Variables: camelCase

// Avoid abbreviations
// GOOD
var userProfile = getUserProfile();
// BAD
var usrProf = getUsrProf();

// Use descriptive names
// GOOD
void sendEmailNotification(User user, String message) { }
// BAD
void send(User u, String m) { }

// Prefer final for local variables
void example() {
  final name = 'Alice';  // GOOD
  var age = 30;          // OK if value changes
}

// Use const for compile-time constants
const pi = 3.14159;
const defaultTimeout = Duration(seconds: 30);

// Prefer relative imports for same package
// GOOD
import 'models/user.dart';
// BAD (for same package)
import 'package:my_app/models/user.dart';

// Group imports
// 1. Dart SDK
// 2. Flutter/external packages
// 3. Your package
import 'dart:async';
import 'dart:io';

import 'package:http/http.dart';
import 'package:intl/intl.dart';

import 'models/user.dart';
import 'utils/helpers.dart';
```

### Null Safety Best Practices

```dart
// Prefer non-nullable types
String getName() => 'Alice';  // GOOD
String? getName() => 'Alice'; // Avoid if possible

// Use late for initialization guarantee
class ConfigManager {
  late final String apiUrl;
  
  void initialize() {
    apiUrl = 'https://api.example.com';
  }
}

// Use ?? for default values
String getDisplayName(String? userName) {
  return userName ?? 'Guest';
}

// Use ?. for safe navigation
void printLength(String? text) {
  print(text?.length ?? 0);
}

// Promote nullable to non-nullable
void process(String? input) {
  if (input != null) {
    // input is promoted to String here
    print(input.length);
  }
}

// Use required for named parameters
void createUser({
  required String name,
  required String email,
  String? phone,
}) { }

// Avoid ! when possible
String? getUserName() => 'Alice';

void example() {
  // BAD (risky)
  var name = getUserName()!;
  
  // GOOD
  var name = getUserName();
  if (name != null) {
    print(name);
  }
}
```

### Error Handling

```dart
// Use specific exception types
class ValidationException implements Exception {
  final String message;
  ValidationException(this.message);
  
  @override
  String toString() => 'ValidationException: $message';
}

// Catch specific exceptions
void processData(String data) {
  try {
    // Process
    if (data.isEmpty) {
      throw ValidationException('Data cannot be empty');
    }
  } on ValidationException catch (e) {
    print('Validation failed: $e');
    rethrow;
  } on FormatException catch (e) {
    print('Format error: $e');
  } catch (e, stackTrace) {
    print('Unexpected error: $e');
    print('Stack trace: $stackTrace');
  }
}

// Return results instead of throwing for expected cases
class Result<T> {
  final T? value;
  final String? error;
  
  Result.success(this.value) : error = null;
  Result.failure(this.error) : value = null;
  
  bool get isSuccess => error == null;
}

Result<int> parseAge(String input) {
  try {
    var age = int.parse(input);
    if (age < 0 || age > 150) {
      return Result.failure('Invalid age range');
    }
    return Result.success(age);
  } catch (e) {
    return Result.failure('Invalid number format');
  }
}
```

### Performance

```dart
// Use const constructors when possible
class Config {
  final String apiUrl;
  final int timeout;
  
  const Config(this.apiUrl, this.timeout);
}

const devConfig = Config('https://dev.api.com', 30);

// Avoid creating objects in loops
// BAD
for (var i = 0; i < 1000; i++) {
  var temp = StringBuffer();
  temp.write(i);
}

// GOOD
var buffer = StringBuffer();
for (var i = 0; i < 1000; i++) {
  buffer.write(i);
}

// Use StringBuffer for string concatenation
// BAD
var result = '';
for (var i = 0; i < 100; i++) {
  result += i.toString();
}

// GOOD
var buffer = StringBuffer();
for (var i = 0; i < 100; i++) {
  buffer.write(i);
}
var result = buffer.toString();

// Cache expensive computations
class DataProcessor {
  final Map<String, dynamic> _cache = {};
  
  dynamic process(String key) {
    return _cache.putIfAbsent(key, () => _expensiveComputation(key));
  }
  
  dynamic _expensiveComputation(String key) {
    // Expensive operation
    return key.hashCode;
  }
}

// Use lazy initialization
class ExpensiveResource {
  static final ExpensiveResource _instance = ExpensiveResource._internal();
  
  factory ExpensiveResource() => _instance;
  
  ExpensiveResource._internal();
}
```

### Async Best Practices

```dart
// Prefer async/await over then()
// GOOD
Future<String> fetchData() async {
  final response = await httpClient.get(url);
  return response.body;
}

// LESS READABLE
Future<String> fetchData() {
  return httpClient.get(url).then((response) => response.body);
}

// Don't await unnecessarily
// BAD
Future<int> getValue() async {
  return 42; // No need for async here
}

// GOOD
Future<int> getValue() {
  return Future.value(42);
}
// OR
int getValue() {
  return 42; // Even better if synchronous is OK
}

// Use Future.wait for parallel operations
Future<void> loadData() async {
  // BAD (sequential)
  final user = await fetchUser();
  final posts = await fetchPosts();
  final comments = await fetchComments();
  
  // GOOD (parallel)
  final results = await Future.wait([
    fetchUser(),
    fetchPosts(),
    fetchComments(),
  ]);
}

// Handle async errors properly
Future<void> processData() async {
  try {
    final data = await fetchData();
    await saveData(data);
  } catch (e) {
    print('Error: $e');
    // Handle or rethrow
  }
}

// Close streams and controllers
class DataService {
  final _controller = StreamController<String>();
  
  Stream<String> get dataStream => _controller.stream;
  
  void dispose() {
    _controller.close(); // Important!
  }
}
```

### Code Organization

```dart
// File structure example:
/*
lib/
  src/
    models/
      user.dart
      post.dart
    services/
      api_service.dart
      auth_service.dart
    utils/
      validators.dart
      helpers.dart
    widgets/
      user_card.dart
  main.dart

test/
  models/
    user_test.dart
  services/
    api_service_test.dart
*/

// Single responsibility
// BAD
class UserManager {
  void createUser() { }
  void deleteUser() { }
  void sendEmail() { }
  void generateReport() { }
}

// GOOD
class UserService {
  void createUser() { }
  void deleteUser() { }
}

class EmailService {
  void sendEmail() { }
}

class ReportGenerator {
  void generateReport() { }
}

// Dependency injection
class UserController {
  final UserService userService;
  final EmailService emailService;
  
  UserController({
    required this.userService,
    required this.emailService,
  });
  
  Future<void> registerUser(User user) async {
    await userService.createUser(user);
    await emailService.sendWelcomeEmail(user);
  }
}
```

## 12. Conclusion

### Key Takeaways

Dart is a powerful, modern programming language that excels in:

1. **Type Safety**: Strong type system with null safety ensures fewer runtime errors
2. **Performance**: AOT and JIT compilation provide excellent performance
3. **Async Programming**: First-class support for futures and streams
4. **Object-Oriented**: Clean OOP with mixins and interfaces
5. **Functional**: Support for functional programming patterns
6. **Tooling**: Excellent development tools and package ecosystem
7. **Cross-Platform**: Write once, run everywhere with Flutter

### Learning Path

1. **Basics**: Master syntax, types, and control flow
2. **OOP**: Understand classes, inheritance, and mixins
3. **Async**: Learn futures, streams, and async/await
4. **Collections**: Use built-in data structures effectively
5. **Best Practices**: Follow Dart conventions and patterns
6. **Testing**: Write comprehensive tests
7. **Packages**: Leverage the pub.dev ecosystem
8. **Flutter**: Build cross-platform applications

### Resources

- **Official Documentation**: dart.dev
- **API Reference**: api.dart.dev
- **Packages**: pub.dev
- **DartPad**: Online playground at dartpad.dev
- **Community**: Discord, Reddit, Stack Overflow

### Next Steps

1. Build real projects to practice
2. Contribute to open-source Dart packages
3. Learn Flutter for UI development
4. Explore server-side Dart with shelf or conduit
5. Study design patterns in Dart context
6. Join the Dart community

### Practice Example: Complete Application

```dart
// A complete example: Todo application

import 'dart:convert';

class Todo {
  final String id;
  String title;
  bool completed;
  DateTime createdAt;
  
  Todo({
    required this.id,
    required this.title,
    this.completed = false,
    required this.createdAt,
  });
  
  Map<String, dynamic> toJson() => {
    'id': id,
    'title': title,
    'completed': completed,
    'createdAt': createdAt.toIso8601String(),
  };
  
  factory Todo.fromJson(Map<String, dynamic> json) => Todo(
    id: json['id'],
    title: json['title'],
    completed: json['completed'],
    createdAt: DateTime.parse(json['createdAt']),
  );
}

class TodoService {
  final List<Todo> _todos = [];
  
  List<Todo> get todos => List.unmodifiable(_todos);
  
  void addTodo(Todo todo) {
    _todos.add(todo);
  }
  
  void removeTodo(String id) {
    _todos.removeWhere((todo) => todo.id == id);
  }
  
  void toggleTodo(String id) {
    final todo = _todos.firstWhere((t) => t.id == id);
    todo.completed = !todo.completed;
  }
  
  List<Todo> getCompleted() {
    return _todos.where((t) => t.completed).toList();
  }
  
  List<Todo> getPending() {
    return _todos.where((t) => !t.completed).toList();
  }
  
  String exportToJson() {
    return jsonEncode(_todos.map((t) => t.toJson()).toList());
  }
  
  void importFromJson(String jsonString) {
    final List<dynamic> data = jsonDecode(jsonString);
    _todos.clear();
    _todos.addAll(data.map((json) => Todo.fromJson(json)));
  }
}

void main() {
  final service = TodoService();
  
  // Add todos
  service.addTodo(Todo(
    id: '1',
    title: 'Learn Dart',
    createdAt: DateTime.now(),
  ));
  
  service.addTodo(Todo(
    id: '2',
    title: 'Build Flutter app',
    createdAt: DateTime.now(),
  ));
  
  // Toggle completion
  service.toggleTodo('1');
  
  // Display todos
  print('All Todos:');
  for (var todo in service.todos) {
    print('${todo.completed ? '✓' : '○'} ${todo.title}');
  }
  
  print('\nCompleted:');
  for (var todo in service.getCompleted()) {
    print('✓ ${todo.title}');
  }
  
  print('\nPending:');
  for (var todo in service.getPending()) {
    print('○ ${todo.title}');
  }
  
  // Export
  final json = service.exportToJson();
  print('\nExported JSON:\n$json');
}
```

This guide covers the essential aspects of Dart programming. Continue exploring, building projects, and engaging with the community to master the language!
