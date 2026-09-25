# JavaScript & TypeScript Programming Language Proficiency Guide

## 1. Introduction

JavaScript is the programming language of the web, and TypeScript is JavaScript with syntax for types. Together, they form the backbone of modern web development, from frontend interfaces to backend services.

### Key Characteristics

**JavaScript:**
- **Dynamic typing**: Variables can hold any type
- **Interpreted**: Runs in browsers and Node.js
- **Multi-paradigm**: Supports OOP, functional, and imperative styles
- **Event-driven**: Built for asynchronous programming
- **Ubiquitous**: Runs everywhere - browsers, servers, mobile, desktop

**TypeScript:**
- **Static typing**: Catch errors at compile time
- **Superset of JavaScript**: All JS code is valid TS
- **Modern features**: Latest ECMAScript features
- **Better tooling**: Enhanced IDE support and autocompletion
- **Compiles to JavaScript**: Works anywhere JS works

### Why Learn JavaScript/TypeScript?

- **Web development**: Essential for frontend and backend
- **Universal**: One language for full-stack development
- **Huge ecosystem**: npm has over 2 million packages
- **Career opportunities**: Most in-demand programming language
- **Versatility**: Web, mobile (React Native), desktop (Electron), IoT

### Setting Up

```bash
# Install Node.js (includes npm)
# Download from nodejs.org or use package manager

# Verify installation
node --version
npm --version

# Install TypeScript
npm install -g typescript

# Verify TypeScript
tsc --version

# Create a project
mkdir my-project
cd my-project
npm init -y

# Initialize TypeScript
tsc --init
```

### Hello World

**JavaScript:**
```javascript
// hello.js
console.log('Hello, JavaScript!');

// Run with:
// node hello.js
```

**TypeScript:**
```typescript
// hello.ts
const greeting: string = 'Hello, TypeScript!';
console.log(greeting);

// Compile and run:
// tsc hello.ts
// node hello.js
```

## 2. Core Language Mechanics

### Syntax Fundamentals

```javascript
// Comments
// Single-line comment
/* Multi-line
   comment */

// Statements (semicolons optional but recommended)
let x = 5;
console.log(x);

// Code blocks
if (true) {
  console.log('Block statement');
}

// Strict mode (recommended)
'use strict';
```

### Variables and Constants

```javascript
// var (function-scoped, avoid in modern code)
var oldWay = 'old';

// let (block-scoped, mutable)
let count = 0;
count = 1; // OK

// const (block-scoped, immutable binding)
const PI = 3.14159;
// PI = 3.14; // ERROR

// const with objects (reference is immutable, not content)
const person = { name: 'Alice' };
person.name = 'Bob'; // OK
person.age = 30;     // OK
// person = {};      // ERROR

// Destructuring
const [a, b, c] = [1, 2, 3];
const { name, age } = { name: 'Alice', age: 30 };

// Spread operator
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5];

const obj1 = { x: 1, y: 2 };
const obj2 = { ...obj1, z: 3 };
```

**TypeScript:**
```typescript
// Explicit type annotations
let name: string = 'Alice';
let age: number = 30;
let isActive: boolean = true;
let values: number[] = [1, 2, 3];
let tuple: [string, number] = ['Alice', 30];

// Type inference
let inferred = 'Hello'; // Type: string
let num = 42;           // Type: number

// Union types
let id: string | number;
id = 'ABC123';
id = 123;

// Type aliases
type ID = string | number;
type Point = { x: number; y: number };

// Literal types
let direction: 'north' | 'south' | 'east' | 'west';
direction = 'north'; // OK
// direction = 'up'; // ERROR
```

### Data Types

```javascript
// Primitive types
let num = 42;                    // Number
let float = 3.14;                // Number
let str = 'Hello';               // String
let bool = true;                 // Boolean
let nothing = null;              // Null
let notDefined = undefined;      // Undefined
let sym = Symbol('unique');      // Symbol
let big = 9007199254740991n;     // BigInt

// typeof operator
console.log(typeof 42);          // 'number'
console.log(typeof 'hello');     // 'string'
console.log(typeof true);        // 'boolean'
console.log(typeof undefined);   // 'undefined'
console.log(typeof null);        // 'object' (historical bug)
console.log(typeof Symbol());    // 'symbol'
console.log(typeof 10n);         // 'bigint'

// Numbers
let integer = 42;
let decimal = 3.14;
let hex = 0xFF;
let binary = 0b1010;
let octal = 0o17;
let scientific = 1.23e5;

// Special number values
let infinity = Infinity;
let negInfinity = -Infinity;
let notANumber = NaN;

// Number methods
Number.isNaN(NaN);              // true
Number.isFinite(42);            // true
Number.isInteger(42);           // true
Number.parseFloat('3.14');      // 3.14
Number.parseInt('42', 10);      // 42

// Strings
let single = 'Single quotes';
let double = "Double quotes";
let template = `Template literal with ${num}`;

// Multi-line strings
let multiLine = `
  Line 1
  Line 2
  Line 3
`;

// String methods
str.length;
str.toUpperCase();
str.toLowerCase();
str.trim();
str.split(',');
str.includes('ell');
str.startsWith('He');
str.endsWith('lo');
str.slice(0, 3);
str.substring(0, 3);
str.replace('Hello', 'Hi');
str.charAt(0);
str.charCodeAt(0);

// Template literals
const name = 'Alice';
const age = 30;
console.log(`${name} is ${age} years old`);
console.log(`Next year: ${age + 1}`);

// Booleans
let isTrue = true;
let isFalse = false;

// Truthy and falsy values
// Falsy: false, 0, '', null, undefined, NaN
// Truthy: everything else

// Arrays
let arr = [1, 2, 3, 4, 5];
let mixed = [1, 'two', true, null];

// Objects
let obj = {
  name: 'Alice',
  age: 30,
  greet() {
    console.log('Hello!');
  }
};
```

**TypeScript:**
```typescript
// Type annotations
let count: number = 42;
let message: string = 'Hello';
let active: boolean = true;

// Array types
let numbers: number[] = [1, 2, 3];
let strings: Array<string> = ['a', 'b', 'c'];

// Tuple types
let tuple: [string, number] = ['Alice', 30];

// Enum types
enum Color {
  Red,
  Green,
  Blue
}

let color: Color = Color.Red;

enum Status {
  Active = 'ACTIVE',
  Inactive = 'INACTIVE',
  Pending = 'PENDING'
}

// Any type (escape hatch, avoid when possible)
let anything: any = 'string';
anything = 42;
anything = true;

// Unknown type (type-safe any)
let value: unknown = 'hello';
// value.toUpperCase(); // ERROR
if (typeof value === 'string') {
  value.toUpperCase(); // OK
}

// Void type
function logMessage(): void {
  console.log('Message');
}

// Never type (functions that never return)
function throwError(): never {
  throw new Error('Error occurred');
}

// Object types
interface Person {
  name: string;
  age: number;
  email?: string; // Optional property
}

let person: Person = {
  name: 'Alice',
  age: 30
};

// Type assertions
let someValue: unknown = 'hello';
let strLength: number = (someValue as string).length;
// or
let strLength2: number = (<string>someValue).length;
```

### Operators

```javascript
// Arithmetic
console.log(5 + 3);    // 8
console.log(5 - 3);    // 2
console.log(5 * 3);    // 15
console.log(5 / 3);    // 1.666...
console.log(5 % 3);    // 2
console.log(5 ** 3);   // 125 (exponentiation)

// Increment/Decrement
let x = 5;
console.log(++x);      // 6 (pre-increment)
console.log(x++);      // 6 (post-increment)
console.log(x);        // 7

// Assignment
let a = 5;
a += 3;  // a = a + 3
a -= 2;  // a = a - 2
a *= 2;  // a = a * 2
a /= 2;  // a = a / 2
a %= 2;  // a = a % 2
a **= 2; // a = a ** 2

// Comparison
console.log(5 == '5');   // true (loose equality)
console.log(5 === '5');  // false (strict equality)
console.log(5 != '5');   // false
console.log(5 !== '5');  // true
console.log(5 > 3);      // true
console.log(5 < 3);      // false
console.log(5 >= 3);     // true
console.log(5 <= 3);     // false

// Logical
console.log(true && false);  // false (AND)
console.log(true || false);  // true (OR)
console.log(!true);          // false (NOT)

// Nullish coalescing
let value = null ?? 'default';  // 'default'
let value2 = 0 ?? 'default';    // 0

// Optional chaining
let user = { profile: { name: 'Alice' } };
console.log(user?.profile?.name);     // 'Alice'
console.log(user?.settings?.theme);   // undefined

// Ternary
let result = age >= 18 ? 'adult' : 'minor';

// Bitwise
console.log(5 & 3);    // 1 (AND)
console.log(5 | 3);    // 7 (OR)
console.log(5 ^ 3);    // 6 (XOR)
console.log(~5);       // -6 (NOT)
console.log(5 << 1);   // 10 (left shift)
console.log(5 >> 1);   // 2 (right shift)
console.log(5 >>> 1);  // 2 (unsigned right shift)

// typeof and instanceof
console.log(typeof 42);              // 'number'
console.log([] instanceof Array);    // true

// Spread and rest
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5];

function sum(...numbers) {
  return numbers.reduce((a, b) => a + b, 0);
}
```

### Type System (TypeScript)

```typescript
// Primitive types
let str: string = 'hello';
let num: number = 42;
let bool: boolean = true;
let nothing: null = null;
let undef: undefined = undefined;

// Array types
let numbers: number[] = [1, 2, 3];
let strings: Array<string> = ['a', 'b'];

// Object types
let obj: { name: string; age: number } = {
  name: 'Alice',
  age: 30
};

// Function types
let add: (a: number, b: number) => number;
add = (x, y) => x + y;

// Union types
let id: string | number;
id = 'ABC123';
id = 123;

// Intersection types
type Named = { name: string };
type Aged = { age: number };
type Person = Named & Aged;

let person: Person = { name: 'Alice', age: 30 };

// Type guards
function isString(value: unknown): value is string {
  return typeof value === 'string';
}

function processValue(value: string | number) {
  if (typeof value === 'string') {
    console.log(value.toUpperCase());
  } else {
    console.log(value.toFixed(2));
  }
}

// Generic types
function identity<T>(arg: T): T {
  return arg;
}

let output = identity<string>('hello');
let number = identity(42); // Type inference

// Generic constraints
interface HasLength {
  length: number;
}

function logLength<T extends HasLength>(arg: T): void {
  console.log(arg.length);
}

logLength('hello');
logLength([1, 2, 3]);
// logLength(42); // ERROR: number doesn't have length

// Utility types
type Partial<T> = { [P in keyof T]?: T[P] };
type Required<T> = { [P in keyof T]-?: T[P] };
type Readonly<T> = { readonly [P in keyof T]: T[P] };
type Pick<T, K extends keyof T> = { [P in K]: T[P] };
type Omit<T, K extends keyof T> = Pick<T, Exclude<keyof T, K>>;

interface User {
  id: number;
  name: string;
  email: string;
}

type PartialUser = Partial<User>;
type UserName = Pick<User, 'name'>;
type UserWithoutEmail = Omit<User, 'email'>;
```

## 3. Control Flow

### Conditional Statements

```javascript
// if-else
let age = 20;
if (age < 18) {
  console.log('Minor');
} else if (age < 65) {
  console.log('Adult');
} else {
  console.log('Senior');
}

// Ternary operator
let status = age >= 18 ? 'Adult' : 'Minor';

// Switch statement
let day = 'Monday';
switch (day) {
  case 'Monday':
    console.log('Start of week');
    break;
  case 'Friday':
    console.log('End of week');
    break;
  case 'Saturday':
  case 'Sunday':
    console.log('Weekend');
    break;
  default:
    console.log('Midweek');
}

// Switch with return (no break needed)
function getDayType(day) {
  switch (day) {
    case 'Saturday':
    case 'Sunday':
      return 'Weekend';
    default:
      return 'Weekday';
  }
}

// Truthy/falsy checks
if (value) {
  // value is truthy
}

if (!value) {
  // value is falsy
}

// Nullish check
if (value === null || value === undefined) {
  // handle null/undefined
}

// Short-circuit evaluation
let name = userName || 'Guest';
let theme = userTheme ?? 'light';

// Guard clauses
function processUser(user) {
  if (!user) return;
  if (!user.email) return;
  
  // Process user
  console.log(user.email);
}
```

**TypeScript:**
```typescript
// Type narrowing with conditionals
function process(value: string | number) {
  if (typeof value === 'string') {
    // value is string here
    console.log(value.toUpperCase());
  } else {
    // value is number here
    console.log(value.toFixed(2));
  }
}

// Discriminated unions
type Shape =
  | { kind: 'circle'; radius: number }
  | { kind: 'square'; size: number }
  | { kind: 'rectangle'; width: number; height: number };

function getArea(shape: Shape): number {
  switch (shape.kind) {
    case 'circle':
      return Math.PI * shape.radius ** 2;
    case 'square':
      return shape.size ** 2;
    case 'rectangle':
      return shape.width * shape.height;
  }
}

// Exhaustiveness checking
function assertNever(x: never): never {
  throw new Error('Unexpected value: ' + x);
}

function processShape(shape: Shape): number {
  switch (shape.kind) {
    case 'circle':
      return Math.PI * shape.radius ** 2;
    case 'square':
      return shape.size ** 2;
    case 'rectangle':
      return shape.width * shape.height;
    default:
      return assertNever(shape); // Compile error if not exhaustive
  }
}
```

### Loops

```javascript
// for loop
for (let i = 0; i < 5; i++) {
  console.log(i);
}

// for...of (iterate over values)
const fruits = ['apple', 'banana', 'orange'];
for (const fruit of fruits) {
  console.log(fruit);
}

// for...in (iterate over keys/indices)
for (const index in fruits) {
  console.log(index, fruits[index]);
}

// For objects
const person = { name: 'Alice', age: 30 };
for (const key in person) {
  console.log(key, person[key]);
}

// while loop
let count = 0;
while (count < 5) {
  console.log(count);
  count++;
}

// do...while loop
let num = 0;
do {
  console.log(num);
  num++;
} while (num < 5);

// break and continue
for (let i = 0; i < 10; i++) {
  if (i === 3) continue; // Skip 3
  if (i === 7) break;    // Stop at 7
  console.log(i);
}

// Labeled statements
outer: for (let i = 0; i < 3; i++) {
  for (let j = 0; j < 3; j++) {
    if (i === 1 && j === 1) break outer;
    console.log(i, j);
  }
}

// Array iteration methods
const numbers = [1, 2, 3, 4, 5];

// forEach
numbers.forEach((num, index) => {
  console.log(index, num);
});

// map
const doubled = numbers.map(num => num * 2);

// filter
const evens = numbers.filter(num => num % 2 === 0);

// reduce
const sum = numbers.reduce((acc, num) => acc + num, 0);

// find
const found = numbers.find(num => num > 3);

// some
const hasEven = numbers.some(num => num % 2 === 0);

// every
const allPositive = numbers.every(num => num > 0);
```

### Exception Handling

```javascript
// Basic try-catch
try {
  const result = riskyOperation();
  console.log(result);
} catch (error) {
  console.error('Error:', error.message);
}

// Finally block
try {
  openFile();
  processFile();
} catch (error) {
  handleError(error);
} finally {
  closeFile(); // Always runs
}

// Throwing errors
function divide(a, b) {
  if (b === 0) {
    throw new Error('Division by zero');
  }
  return a / b;
}

// Custom error classes
class ValidationError extends Error {
  constructor(message) {
    super(message);
    this.name = 'ValidationError';
  }
}

class NetworkError extends Error {
  constructor(message, statusCode) {
    super(message);
    this.name = 'NetworkError';
    this.statusCode = statusCode;
  }
}

// Catching specific errors
try {
  validateInput(data);
} catch (error) {
  if (error instanceof ValidationError) {
    console.log('Validation failed:', error.message);
  } else if (error instanceof NetworkError) {
    console.log('Network error:', error.statusCode);
  } else {
    console.log('Unknown error:', error);
  }
}

// Rethrowing errors
try {
  try {
    dangerousOperation();
  } catch (error) {
    console.log('Logging error');
    throw error; // Rethrow
  }
} catch (error) {
  console.log('Outer catch:', error);
}

// Async error handling
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Failed to fetch data:', error);
    throw error;
  }
}

// Promise error handling
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error))
  .finally(() => console.log('Done'));
```

**TypeScript:**
```typescript
// Error types
class ValidationError extends Error {
  constructor(public field: string, message: string) {
    super(message);
    this.name = 'ValidationError';
  }
}

// Type-safe error handling
function processData(data: unknown): string {
  try {
    if (typeof data !== 'string') {
      throw new ValidationError('data', 'Must be a string');
    }
    return data.toUpperCase();
  } catch (error) {
    if (error instanceof ValidationError) {
      console.log(`Validation error in ${error.field}: ${error.message}`);
      throw error;
    }
    throw error;
  }
}

// Result type pattern
type Result<T, E = Error> =
  | { success: true; value: T }
  | { success: false; error: E };

function divide(a: number, b: number): Result<number> {
  if (b === 0) {
    return { success: false, error: new Error('Division by zero') };
  }
  return { success: true, value: a / b };
}

const result = divide(10, 2);
if (result.success) {
  console.log(result.value);
} else {
  console.error(result.error);
}
```

## 4. Functions and Code Organization

### Function Basics

```javascript
// Function declaration
function add(a, b) {
  return a + b;
}

// Function expression
const multiply = function(a, b) {
  return a * b;
};

// Arrow function
const subtract = (a, b) => a - b;

// Arrow function with block
const divide = (a, b) => {
  if (b === 0) {
    throw new Error('Division by zero');
  }
  return a / b;
};

// Single parameter (parentheses optional)
const square = x => x * x;

// No parameters
const greet = () => console.log('Hello!');

// Default parameters
function power(base, exponent = 2) {
  return base ** exponent;
}

console.log(power(2));     // 4
console.log(power(2, 3));  // 8

// Rest parameters
function sum(...numbers) {
  return numbers.reduce((acc, num) => acc + num, 0);
}

console.log(sum(1, 2, 3, 4, 5)); // 15

// Destructuring parameters
function printUser({ name, age, email = 'none' }) {
  console.log(`${name}, ${age}, ${email}`);
}

printUser({ name: 'Alice', age: 30 });

// Immediately Invoked Function Expression (IIFE)
(function() {
  console.log('Executed immediately');
})();

// Arrow IIFE
(() => {
  console.log('Arrow IIFE');
})();

// Named function expression
const factorial = function fact(n) {
  if (n <= 1) return 1;
  return n * fact(n - 1);
};
```

**TypeScript:**
```typescript
// Function with types
function add(a: number, b: number): number {
  return a + b;
}

// Optional parameters
function greet(name: string, greeting?: string): string {
  return `${greeting || 'Hello'}, ${name}!`;
}

// Default parameters
function multiply(a: number, b: number = 1): number {
  return a * b;
}

// Rest parameters with types
function sum(...numbers: number[]): number {
  return numbers.reduce((acc, num) => acc + num, 0);
}

// Function type
type MathOperation = (a: number, b: number) => number;

const subtract: MathOperation = (a, b) => a - b;

// Function overloading
function process(value: string): string;
function process(value: number): number;
function process(value: string | number): string | number {
  if (typeof value === 'string') {
    return value.toUpperCase();
  }
  return value * 2;
}

// Generic functions
function identity<T>(arg: T): T {
  return arg;
}

function getFirst<T>(arr: T[]): T | undefined {
  return arr[0];
}

// Void and never return types
function log(message: string): void {
  console.log(message);
}

function throwError(message: string): never {
  throw new Error(message);
}

// Callback types
function fetchData(callback: (error: Error | null, data: string) => void): void {
  setTimeout(() => {
    callback(null, 'data');
  }, 1000);
}

// Promise return type
async function fetchUser(): Promise<User> {
  const response = await fetch('/api/user');
  return response.json();
}
```

### Higher-Order Functions

```javascript
// Function as parameter
function executeOperation(a, b, operation) {
  return operation(a, b);
}

console.log(executeOperation(5, 3, (a, b) => a + b));  // 8
console.log(executeOperation(5, 3, (a, b) => a * b));  // 15

// Function returning function
function makeMultiplier(factor) {
  return function(number) {
    return number * factor;
  };
}

const double = makeMultiplier(2);
const triple = makeMultiplier(3);

console.log(double(5));  // 10
console.log(triple(5));  // 15

// Currying
function curry(fn) {
  return function curried(...args) {
    if (args.length >= fn.length) {
      return fn.apply(this, args);
    }
    return function(...nextArgs) {
      return curried.apply(this, [...args, ...nextArgs]);
    };
  };
}

const add = (a, b, c) => a + b + c;
const curriedAdd = curry(add);

console.log(curriedAdd(1)(2)(3));     // 6
console.log(curriedAdd(1, 2)(3));     // 6
console.log(curriedAdd(1)(2, 3));     // 6

// Composition
const compose = (...fns) => x => 
  fns.reduceRight((acc, fn) => fn(acc), x);

const pipe = (...fns) => x => 
  fns.reduce((acc, fn) => fn(acc), x);

const addOne = x => x + 1;
const double = x => x * 2;
const square = x => x * x;

const composed = compose(square, double, addOne);
console.log(composed(5)); // ((5 + 1) * 2) ** 2 = 144

const piped = pipe(addOne, double, square);
console.log(piped(5)); // same result

// Memoization
function memoize(fn) {
  const cache = new Map();
  return function(...args) {
    const key = JSON.stringify(args);
    if (cache.has(key)) {
      return cache.get(key);
    }
    const result = fn.apply(this, args);
    cache.set(key, result);
    return result;
  };
}

const expensiveFunction = memoize((n) => {
  console.log('Computing...');
  return n * 2;
});

console.log(expensiveFunction(5)); // Computing... 10
console.log(expensiveFunction(5)); // 10 (cached)

// Partial application
function partial(fn, ...args) {
  return function(...moreArgs) {
    return fn(...args, ...moreArgs);
  };
}

const addNumbers = (a, b, c) => a + b + c;
const add5 = partial(addNumbers, 5);

console.log(add5(3, 2)); // 10
```

### Closures

```javascript
// Basic closure
function makeCounter() {
  let count = 0;
  
  return function() {
    count++;
    return count;
  };
}

const counter = makeCounter();
console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3

// Private variables
function createPerson(name) {
  let age = 0; // Private
  
  return {
    getName() {
      return name;
    },
    getAge() {
      return age;
    },
    setAge(newAge) {
      if (newAge >= 0) {
        age = newAge;
      }
    },
    haveBirthday() {
      age++;
    }
  };
}

const person = createPerson('Alice');
person.setAge(30);
console.log(person.getAge()); // 30
person.haveBirthday();
console.log(person.getAge()); // 31

// Module pattern
const calculator = (function() {
  let result = 0; // Private state
  
  return {
    add(n) {
      result += n;
      return this;
    },
    subtract(n) {
      result -= n;
      return this;
    },
    multiply(n) {
      result *= n;
      return this;
    },
    getResult() {
      return result;
    },
    reset() {
      result = 0;
      return this;
    }
  };
})();

calculator.add(5).multiply(2).subtract(3);
console.log(calculator.getResult()); // 7

// Function factory
function createGreeter(greeting) {
  return function(name) {
    return `${greeting}, ${name}!`;
  };
}

const sayHello = createGreeter('Hello');
const sayHi = createGreeter('Hi');

console.log(sayHello('Alice')); // Hello, Alice!
console.log(sayHi('Bob'));      // Hi, Bob!
```

### Async Functions

```javascript
// Callback pattern (old style)
function fetchDataCallback(callback) {
  setTimeout(() => {
    callback(null, 'data');
  }, 1000);
}

fetchDataCallback((error, data) => {
  if (error) {
    console.error(error);
  } else {
    console.log(data);
  }
});

// Promise-based
function fetchDataPromise() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve('data');
      // reject(new Error('Failed'));
    }, 1000);
  });
}

fetchDataPromise()
  .then(data => console.log(data))
  .catch(error => console.error(error));

// Async/await
async function fetchDataAsync() {
  try {
    const data = await fetchDataPromise();
    console.log(data);
    return data;
  } catch (error) {
    console.error(error);
    throw error;
  }
}

// Multiple async operations
async function fetchAll() {
  try {
    // Sequential
    const user = await fetchUser();
    const posts = await fetchPosts(user.id);
    
    // Parallel
    const [users, posts, comments] = await Promise.all([
      fetchUsers(),
      fetchPosts(),
      fetchComments()
    ]);
    
    // Race (first to complete)
    const fastest = await Promise.race([
      fetchFromServer1(),
      fetchFromServer2()
    ]);
    
    // AllSettled (wait for all, don't fail fast)
    const results = await Promise.allSettled([
      fetchData1(),
      fetchData2(),
      fetchData3()
    ]);
    
    results.forEach(result => {
      if (result.status === 'fulfilled') {
        console.log(result.value);
      } else {
        console.error(result.reason);
      }
    });
  } catch (error) {
    console.error(error);
  }
}

// Async iteration
async function* asyncGenerator() {
  for (let i = 0; i < 5; i++) {
    await new Promise(resolve => setTimeout(resolve, 100));
    yield i;
  }
}

(async () => {
  for await (const value of asyncGenerator()) {
    console.log(value);
  }
})();
```

**TypeScript:**
```typescript
// Async function with types
async function fetchUser(id: number): Promise<User> {
  const response = await fetch(`/api/users/${id}`);
  if (!response.ok) {
    throw new Error('Failed to fetch user');
  }
  return response.json();
}

// Promise type
type UserPromise = Promise<User>;

// Async generic function
async function fetchData<T>(url: string): Promise<T> {
  const response = await fetch(url);
  return response.json();
}

const user = await fetchData<User>('/api/user');

// Async callback types
type AsyncCallback<T> = (error: Error | null, result?: T) => void;

function fetchDataWithCallback(callback: AsyncCallback<string>): void {
  setTimeout(() => {
    callback(null, 'data');
  }, 1000);
}
```

## 5. Data Structures

### Arrays

```javascript
// Creating arrays
const arr1 = [1, 2, 3, 4, 5];
const arr2 = new Array(5); // [empty × 5]
const arr3 = new Array(1, 2, 3); // [1, 2, 3]
const arr4 = Array.from('hello'); // ['h', 'e', 'l', 'l', 'o']
const arr5 = Array.from({ length: 5 }, (_, i) => i); // [0, 1, 2, 3, 4]
const arr6 = [...arr1]; // Copy array

// Array properties and methods
const numbers = [1, 2, 3, 4, 5];

// Length
console.log(numbers.length); // 5

// Adding elements
numbers.push(6);        // Add to end
numbers.unshift(0);     // Add to start
numbers.splice(3, 0, 2.5); // Insert at index 3

// Removing elements
numbers.pop();          // Remove from end
numbers.shift();        // Remove from start
numbers.splice(2, 1);   // Remove at index 2

// Access
console.log(numbers[0]);        // First element
console.log(numbers.at(-1));    // Last element
console.log(numbers.at(-2));    // Second to last

// Slicing and copying
const slice = numbers.slice(1, 4);      // Elements 1-3
const copy = [...numbers];               // Shallow copy
const copy2 = Array.from(numbers);       // Shallow copy

// Searching
console.log(numbers.includes(3));       // true
console.log(numbers.indexOf(3));        // Index of 3
console.log(numbers.lastIndexOf(2));    // Last index of 2
console.log(numbers.find(n => n > 3));  // First match
console.log(numbers.findIndex(n => n > 3)); // Index of first match

// Transformation
const doubled = numbers.map(n => n * 2);
const evens = numbers.filter(n => n % 2 === 0);
const sum = numbers.reduce((acc, n) => acc + n, 0);
const flattened = [[1, 2], [3, 4]].flat();
const flatMapped = [1, 2, 3].flatMap(n => [n, n * 2]);

// Sorting
const unsorted = [3, 1, 4, 1, 5, 9, 2, 6];
unsorted.sort(); // Modifies array
unsorted.sort((a, b) => a - b); // Numeric sort
unsorted.sort((a, b) => b - a); // Reverse numeric sort

const words = ['banana', 'apple', 'cherry'];
words.sort(); // Alphabetical

// Reversing
numbers.reverse(); // Modifies array

// Joining
console.log(numbers.join(', ')); // '1, 2, 3, 4, 5'
console.log(numbers.join('')); // '12345'

// Checking
console.log(numbers.every(n => n > 0));     // true
console.log(numbers.some(n => n > 10));     // false

// Iteration
numbers.forEach((num, index) => {
  console.log(index, num);
});

for (const num of numbers) {
  console.log(num);
}

for (const [index, num] of numbers.entries()) {
  console.log(index, num);
}

// Filling
const arr = new Array(5).fill(0);     // [0, 0, 0, 0, 0]
const arr2 = Array(5).fill(0, 2, 4);  // [empty, empty, 0, 0, empty]

// Concatenation
const arr7 = [1, 2].concat([3, 4], [5, 6]);
const arr8 = [...[1, 2], ...[3, 4], ...[5, 6]];

// Destructuring
const [first, second, ...rest] = [1, 2, 3, 4, 5];
console.log(first, second, rest); // 1 2 [3, 4, 5]

// Multi-dimensional arrays
const matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];

console.log(matrix[1][2]); // 6

// Array-like objects
const arrayLike = { 0: 'a', 1: 'b', 2: 'c', length: 3 };
const arr9 = Array.from(arrayLike);
```

**TypeScript:**
```typescript
// Typed arrays
const numbers: number[] = [1, 2, 3];
const strings: Array<string> = ['a', 'b', 'c'];

// Readonly arrays
const readonlyNumbers: readonly number[] = [1, 2, 3];
const readonlyStrings: ReadonlyArray<string> = ['a', 'b', 'c'];
// readonlyNumbers.push(4); // ERROR

// Tuple types
const tuple: [string, number] = ['Alice', 30];
const tuple2: [string, number, boolean?] = ['Bob', 25];

// Readonly tuple
const readonlyTuple: readonly [string, number] = ['Alice', 30];

// Array destructuring with types
const [first, second]: [number, number] = [1, 2];

// Generic array functions
function getFirstElement<T>(arr: T[]): T | undefined {
  return arr[0];
}

function filterArray<T>(arr: T[], predicate: (item: T) => boolean): T[] {
  return arr.filter(predicate);
}
```

### Objects and Maps

```javascript
// Object creation
const obj1 = { name: 'Alice', age: 30 };
const obj2 = new Object();
const obj3 = Object.create(null); // No prototype

// Property access
console.log(obj1.name);      // Dot notation
console.log(obj1['age']);    // Bracket notation

// Dynamic properties
const key = 'email';
obj1[key] = 'alice@example.com';

// Computed property names
const prop = 'status';
const obj4 = {
  [prop]: 'active',
  [`is${prop}`]: true
};

// Property shorthand
const name = 'Bob';
const age = 25;
const obj5 = { name, age }; // Same as { name: name, age: age }

// Method shorthand
const obj6 = {
  greet() {
    console.log('Hello!');
  }
};

// Object methods
const person = { name: 'Alice', age: 30, city: 'NYC' };

// Keys, values, entries
console.log(Object.keys(person));        // ['name', 'age', 'city']
console.log(Object.values(person));      // ['Alice', 30, 'NYC']
console.log(Object.entries(person));     // [['name', 'Alice'], ...]

// Check property existence
console.log('name' in person);           // true
console.log(person.hasOwnProperty('name')); // true

// Adding/modifying properties
person.email = 'alice@example.com';
person['phone'] = '555-1234';

// Deleting properties
delete person.city;

// Object destructuring
const { name, age } = person;
const { name: userName, age: userAge } = person; // Rename

// Rest in objects
const { name, ...rest } = person;

// Default values
const { email = 'none' } = person;

// Nested destructuring
const user = {
  id: 1,
  profile: {
    name: 'Alice',
    age: 30
  }
};

const { profile: { name: profileName } } = user;

// Object spread
const obj7 = { a: 1, b: 2 };
const obj8 = { ...obj7, c: 3 }; // { a: 1, b: 2, c: 3 }

// Merging objects
const defaults = { theme: 'light', fontSize: 14 };
const userSettings = { theme: 'dark' };
const finalSettings = { ...defaults, ...userSettings };

// Object.assign
const merged = Object.assign({}, defaults, userSettings);

// Freezing objects
const frozen = Object.freeze({ name: 'Alice' });
// frozen.name = 'Bob'; // Error in strict mode

// Sealing objects
const sealed = Object.seal({ name: 'Alice' });
sealed.name = 'Bob'; // OK
// sealed.age = 30;  // Error

// Property descriptors
Object.defineProperty(obj1, 'id', {
  value: 123,
  writable: false,
  enumerable: true,
  configurable: false
});

// Getters and setters
const obj9 = {
  _value: 0,
  get value() {
    return this._value;
  },
  set value(v) {
    if (v >= 0) this._value = v;
  }
};

// Map (better for key-value pairs)
const map = new Map();

// Set values
map.set('name', 'Alice');
map.set('age', 30);
map.set(42, 'number key');
map.set({ key: 'obj' }, 'object key');

// Get values
console.log(map.get('name')); // 'Alice'
console.log(map.size);        // 4

// Check existence
console.log(map.has('name')); // true

// Delete
map.delete('age');

// Iterate
for (const [key, value] of map) {
  console.log(key, value);
}

map.forEach((value, key) => {
  console.log(key, value);
});

// Convert to/from object
const objFromMap = Object.fromEntries(map);
const mapFromObj = new Map(Object.entries(obj1));

// WeakMap (garbage-collectable keys)
const weakMap = new WeakMap();
let obj10 = { id: 1 };
weakMap.set(obj10, 'metadata');
// obj10 = null; // Object can be GC'd

// Map with initial values
const map2 = new Map([
  ['key1', 'value1'],
  ['key2', 'value2']
]);
```

**TypeScript:**
```typescript
// Object types
interface Person {
  name: string;
  age: number;
  email?: string; // Optional
}

type User = {
  id: number;
  username: string;
  readonly createdAt: Date; // Readonly
};

// Index signatures
interface Dictionary {
  [key: string]: string;
}

const dict: Dictionary = {
  hello: 'world',
  foo: 'bar'
};

// Record type
type UserRecord = Record<string, User>;

const users: UserRecord = {
  user1: { id: 1, username: 'alice', createdAt: new Date() },
  user2: { id: 2, username: 'bob', createdAt: new Date() }
};

// Partial and Required
type PartialPerson = Partial<Person>;
type RequiredPerson = Required<Person>;

// Pick and Omit
type PersonName = Pick<Person, 'name'>;
type PersonWithoutEmail = Omit<Person, 'email'>;

// Map types
const stringMap: Map<string, number> = new Map();
stringMap.set('one', 1);
stringMap.set('two', 2);

// Generic Map
function createMap<K, V>(entries: [K, V][]): Map<K, V> {
  return new Map(entries);
}
```

### Sets

```javascript
// Creating sets
const set1 = new Set();
const set2 = new Set([1, 2, 3, 3, 3]); // {1, 2, 3}
const set3 = new Set('hello'); // {'h', 'e', 'l', 'o'}

// Adding elements
set1.add(1);
set1.add(2);
set1.add(3);
set1.add(2); // Duplicate ignored

// Size
console.log(set1.size); // 3

// Check existence
console.log(set1.has(2)); // true

// Delete
set1.delete(2);

// Clear all
// set1.clear();

// Iteration
for (const value of set1) {
  console.log(value);
}

set1.forEach(value => {
  console.log(value);
});

// Convert to array
const arr = [...set1];
const arr2 = Array.from(set1);

// Set operations
const a = new Set([1, 2, 3, 4]);
const b = new Set([3, 4, 5, 6]);

// Union
const union = new Set([...a, ...b]);
console.log(union); // {1, 2, 3, 4, 5, 6}

// Intersection
const intersection = new Set([...a].filter(x => b.has(x)));
console.log(intersection); // {3, 4}

// Difference
const difference = new Set([...a].filter(x => !b.has(x)));
console.log(difference); // {1, 2}

// Symmetric difference
const symDiff = new Set([
  ...[...a].filter(x => !b.has(x)),
  ...[...b].filter(x => !a.has(x))
]);

// Subset
const isSubset = (subset, superset) =>
  [...subset].every(item => superset.has(item));

// Remove duplicates from array
const numbers = [1, 2, 2, 3, 3, 3, 4, 5, 5];
const unique = [...new Set(numbers)];

// WeakSet (garbage-collectable values)
const weakSet = new WeakSet();
let obj = { id: 1 };
weakSet.add(obj);
// obj = null; // Object can be GC'd
```

**TypeScript:**
```typescript
// Typed sets
const numberSet: Set<number> = new Set([1, 2, 3]);
const stringSet: Set<string> = new Set(['a', 'b', 'c']);

// Generic Set
function removeDuplicates<T>(arr: T[]): T[] {
  return [...new Set(arr)];
}

// ReadonlySet
type ReadonlySet<T> = Omit<Set<T>, 'add' | 'delete' | 'clear'>;

function processSet(set: ReadonlySet<number>): void {
  for (const item of set) {
    console.log(item);
  }
  // set.add(1); // ERROR
}
```

### Typed Arrays

```javascript
// Typed arrays for binary data
const int8 = new Int8Array(8);
const uint8 = new Uint8Array(8);
const int16 = new Int16Array(4);
const uint16 = new Uint16Array(4);
const int32 = new Int32Array(2);
const uint32 = new Uint32Array(2);
const float32 = new Float32Array(4);
const float64 = new Float64Array(2);

// From array
const arr = new Uint8Array([1, 2, 3, 4]);

// Properties
console.log(arr.length);         // 4
console.log(arr.byteLength);     // 4
console.log(arr.BYTES_PER_ELEMENT); // 1

// Methods (similar to regular arrays)
arr.fill(0);
arr.set([10, 20], 0);
const slice = arr.slice(0, 2);

// ArrayBuffer
const buffer = new ArrayBuffer(16);
const view1 = new Int32Array(buffer);
const view2 = new Uint8Array(buffer);

view1[0] = 42;
console.log(view2[0], view2[1], view2[2], view2[3]); // Bytes of 42

// DataView (flexible view)
const dataView = new DataView(buffer);
dataView.setInt32(0, 42, true); // little-endian
dataView.setFloat64(8, 3.14, true);

console.log(dataView.getInt32(0, true));
console.log(dataView.getFloat64(8, true));
```

## 6. Object-Oriented Programming

### Classes

```javascript
// Basic class
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  
  greet() {
    console.log(`Hello, I'm ${this.name}`);
  }
  
  get info() {
    return `${this.name}, ${this.age}`;
  }
  
  set updateAge(newAge) {
    if (newAge >= 0) {
      this.age = newAge;
    }
  }
  
  static species = 'Homo sapiens';
  
  static describe() {
    console.log('Person class');
  }
}

// Creating instances
const alice = new Person('Alice', 30);
alice.greet();
console.log(alice.info);
alice.updateAge = 31;

console.log(Person.species);
Person.describe();

// Private fields and methods (# prefix)
class BankAccount {
  #balance = 0;
  #accountNumber;
  
  constructor(accountNumber) {
    this.#accountNumber = accountNumber;
  }
  
  deposit(amount) {
    if (amount > 0) {
      this.#balance += amount;
      this.#logTransaction('deposit', amount);
    }
  }
  
  withdraw(amount) {
    if (amount > 0 && amount <= this.#balance) {
      this.#balance -= amount;
      this.#logTransaction('withdraw', amount);
      return true;
    }
    return false;
  }
  
  get balance() {
    return this.#balance;
  }
  
  #logTransaction(type, amount) {
    console.log(`${type}: $${amount}`);
  }
}

const account = new BankAccount('123456');
account.deposit(1000);
account.withdraw(250);
console.log(account.balance);
// console.log(account.#balance); // ERROR: private field

// Class expressions
const Rectangle = class {
  constructor(width, height) {
    this.width = width;
    this.height = height;
  }
  
  get area() {
    return this.width * this.height;
  }
};

// Static initialization blocks
class Config {
  static #apiKey;
  
  static {
    // Runs once when class is evaluated
    this.#apiKey = process.env.API_KEY || 'default';
  }
  
  static getApiKey() {
    return this.#apiKey;
  }
}
```

**TypeScript:**
```typescript
// Class with types
class Person {
  name: string;
  private age: number;
  protected email: string;
  readonly id: number;
  
  constructor(name: string, age: number, email: string) {
    this.name = name;
    this.age = age;
    this.email = email;
    this.id = Math.random();
  }
  
  greet(): void {
    console.log(`Hello, I'm ${this.name}`);
  }
  
  getAge(): number {
    return this.age;
  }
}

// Parameter properties (shorthand)
class User {
  constructor(
    public username: string,
    private password: string,
    protected email: string
  ) {}
}

// Abstract classes
abstract class Shape {
  abstract getArea(): number;
  abstract getPerimeter(): number;
  
  describe(): void {
    console.log(`Area: ${this.getArea()}`);
  }
}

class Circle extends Shape {
  constructor(private radius: number) {
    super();
  }
  
  getArea(): number {
    return Math.PI * this.radius ** 2;
  }
  
  getPerimeter(): number {
    return 2 * Math.PI * this.radius;
  }
}

// Interfaces
interface Drawable {
  draw(): void;
}

interface Movable {
  move(x: number, y: number): void;
}

class GameObject implements Drawable, Movable {
  constructor(private x: number = 0, private y: number = 0) {}
  
  draw(): void {
    console.log(`Drawing at (${this.x}, ${this.y})`);
  }
  
  move(x: number, y: number): void {
    this.x = x;
    this.y = y;
  }
}

// Generic classes
class Container<T> {
  private items: T[] = [];
  
  add(item: T): void {
    this.items.push(item);
  }
  
  get(index: number): T | undefined {
    return this.items[index];
  }
  
  getAll(): T[] {
    return [...this.items];
  }
}

const numberContainer = new Container<number>();
numberContainer.add(1);
numberContainer.add(2);
```

### Inheritance

```javascript
// Base class
class Animal {
  constructor(name) {
    this.name = name;
  }
  
  makeSound() {
    console.log('Some generic sound');
  }
  
  eat() {
    console.log(`${this.name} is eating`);
  }
}

// Derived class
class Dog extends Animal {
  constructor(name, breed) {
    super(name); // Call parent constructor
    this.breed = breed;
  }
  
  makeSound() {
    console.log(`${this.name} barks`);
  }
  
  fetch() {
    console.log(`${this.name} is fetching`);
  }
}

const dog = new Dog('Buddy', 'Golden Retriever');
dog.makeSound(); // Buddy barks
dog.eat();       // Buddy is eating
dog.fetch();     // Buddy is fetching

// Multi-level inheritance
class Puppy extends Dog {
  constructor(name, breed) {
    super(name, breed);
    this.age = 0;
  }
  
  play() {
    console.log(`${this.name} is playing`);
  }
}

// Checking inheritance
console.log(dog instanceof Dog);     // true
console.log(dog instanceof Animal);  // true
console.log(dog instanceof Object);  // true

// Super keyword
class Cat extends Animal {
  constructor(name, indoor) {
    super(name);
    this.indoor = indoor;
  }
  
  makeSound() {
    super.makeSound(); // Call parent method
    console.log(`${this.name} meows`);
  }
}
```

**TypeScript:**
```typescript
// Inheritance with types
class Animal {
  constructor(protected name: string, protected age: number) {}
  
  makeSound(): void {
    console.log('Generic sound');
  }
}

class Dog extends Animal {
  constructor(name: string, age: number, private breed: string) {
    super(name, age);
  }
  
  makeSound(): void {
    console.log(`${this.name} barks`);
  }
  
  getBreed(): string {
    return this.breed;
  }
}

// Abstract class inheritance
abstract class Vehicle {
  constructor(protected make: string, protected model: string) {}
  
  abstract start(): void;
  
  stop(): void {
    console.log('Vehicle stopped');
  }
}

class Car extends Vehicle {
  start(): void {
    console.log(`${this.make} ${this.model} started`);
  }
}
```

### Prototypes

```javascript
// Constructor function (old way)
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Adding methods to prototype
Person.prototype.greet = function() {
  console.log(`Hello, I'm ${this.name}`);
};

const person1 = new Person('Alice', 30);
person1.greet();

// Prototype chain
console.log(person1.__proto__ === Person.prototype); // true
console.log(Person.prototype.__proto__ === Object.prototype); // true

// Object.create
const personProto = {
  greet() {
    console.log(`Hello, I'm ${this.name}`);
  }
};

const person2 = Object.create(personProto);
person2.name = 'Bob';
person2.greet();

// Checking prototype
console.log(Object.getPrototypeOf(person1) === Person.prototype); // true

// Setting prototype
const obj = {};
Object.setPrototypeOf(obj, personProto);

// hasOwnProperty
console.log(person1.hasOwnProperty('name')); // true
console.log(person1.hasOwnProperty('greet')); // false (on prototype)

// Property enumeration
for (const key in person1) {
  if (person1.hasOwnProperty(key)) {
    console.log(key, person1[key]);
  }
}
```

### Design Patterns

```javascript
// Singleton
class Singleton {
  static #instance;
  
  static getInstance() {
    if (!Singleton.#instance) {
      Singleton.#instance = new Singleton();
    }
    return Singleton.#instance;
  }
  
  constructor() {
    if (Singleton.#instance) {
      throw new Error('Use Singleton.getInstance()');
    }
  }
}

// Factory
class ShapeFactory {
  static createShape(type, ...args) {
    switch (type) {
      case 'circle':
        return new Circle(...args);
      case 'square':
        return new Square(...args);
      default:
        throw new Error('Unknown shape type');
    }
  }
}

// Builder
class UserBuilder {
  constructor() {
    this.user = {};
  }
  
  setName(name) {
    this.user.name = name;
    return this;
  }
  
  setAge(age) {
    this.user.age = age;
    return this;
  }
  
  setEmail(email) {
    this.user.email = email;
    return this;
  }
  
  build() {
    return this.user;
  }
}

const user = new UserBuilder()
  .setName('Alice')
  .setAge(30)
  .setEmail('alice@example.com')
  .build();

// Observer
class EventEmitter {
  #listeners = {};
  
  on(event, callback) {
    if (!this.#listeners[event]) {
      this.#listeners[event] = [];
    }
    this.#listeners[event].push(callback);
  }
  
  emit(event, ...args) {
    if (this.#listeners[event]) {
      this.#listeners[event].forEach(callback => {
        callback(...args);
      });
    }
  }
  
  off(event, callback) {
    if (this.#listeners[event]) {
      this.#listeners[event] = this.#listeners[event]
        .filter(cb => cb !== callback);
    }
  }
}

// Strategy
class PaymentProcessor {
  constructor(strategy) {
    this.strategy = strategy;
  }
  
  processPayment(amount) {
    return this.strategy.process(amount);
  }
}

class CreditCardStrategy {
  process(amount) {
    console.log(`Processing credit card payment: $${amount}`);
  }
}

class PayPalStrategy {
  process(amount) {
    console.log(`Processing PayPal payment: $${amount}`);
  }
}
```

## 7. Functional Programming Concepts

### Higher-Order Functions

```javascript
// Map, filter, reduce
const numbers = [1, 2, 3, 4, 5];

// Map
const doubled = numbers.map(n => n * 2);
const squared = numbers.map(n => n ** 2);

// Filter
const evens = numbers.filter(n => n % 2 === 0);
const greaterThan2 = numbers.filter(n => n > 2);

// Reduce
const sum = numbers.reduce((acc, n) => acc + n, 0);
const product = numbers.reduce((acc, n) => acc * n, 1);
const max = numbers.reduce((acc, n) => Math.max(acc, n), -Infinity);

// Chaining
const result = numbers
  .filter(n => n % 2 === 0)
  .map(n => n ** 2)
  .reduce((acc, n) => acc + n, 0);

// Find and findIndex
const first = numbers.find(n => n > 3);
const index = numbers.findIndex(n => n > 3);

// Some and every
const hasEven = numbers.some(n => n % 2 === 0);
const allPositive = numbers.every(n => n > 0);

// FlatMap
const nested = [[1, 2], [3, 4], [5]];
const flattened = nested.flatMap(arr => arr.map(n => n * 2));

// Object methods
const obj = { a: 1, b: 2, c: 3 };

Object.keys(obj).forEach(key => {
  console.log(key, obj[key]);
});

const doubled = Object.fromEntries(
  Object.entries(obj).map(([key, value]) => [key, value * 2])
);
```

### Pure Functions

```javascript
// Pure function (no side effects, same input = same output)
function add(a, b) {
  return a + b;
}

function multiply(a, b) {
  return a * b;
}

// Impure function (has side effects)
let total = 0;
function addToTotal(n) {
  total += n; // Modifies external state
  return total;
}

// Pure function examples
function square(n) {
  return n * n;
}

function getFullName(firstName, lastName) {
  return `${firstName} ${lastName}`;
}

function filterEven(numbers) {
  return numbers.filter(n => n % 2 === 0);
}

// Avoiding mutations
function updateUser(user, updates) {
  // BAD: Mutates original
  // user.name = updates.name;
  // return user;
  
  // GOOD: Creates new object
  return { ...user, ...updates };
}

function addItem(array, item) {
  // BAD: Mutates original
  // array.push(item);
  // return array;
  
  // GOOD: Creates new array
  return [...array, item];
}
```

### Immutability

```javascript
// Immutable operations on arrays
const original = [1, 2, 3];

// Add
const withFour = [...original, 4];

// Remove
const withoutTwo = original.filter(n => n !== 2);

// Update
const updated = original.map(n => n === 2 ? 20 : n);

// Immutable operations on objects
const user = { name: 'Alice', age: 30 };

// Add property
const withEmail = { ...user, email: 'alice@example.com' };

// Update property
const older = { ...user, age: 31 };

// Remove property
const { age, ...withoutAge } = user;

// Nested immutable updates
const state = {
  user: {
    profile: {
      name: 'Alice',
      age: 30
    }
  }
};

const newState = {
  ...state,
  user: {
    ...state.user,
    profile: {
      ...state.user.profile,
      age: 31
    }
  }
};

// Using libraries (Immer example concept)
function produce(state, recipe) {
  const draft = JSON.parse(JSON.stringify(state));
  recipe(draft);
  return draft;
}

const updated = produce(state, draft => {
  draft.user.profile.age = 31;
});

// Freezing objects
const frozen = Object.freeze({ name: 'Alice' });
// frozen.name = 'Bob'; // Error in strict mode

// Deep freeze
function deepFreeze(obj) {
  Object.freeze(obj);
  Object.values(obj).forEach(value => {
    if (typeof value === 'object' && value !== null) {
      deepFreeze(value);
    }
  });
  return obj;
}
```

### Composition and Currying

```javascript
// Function composition
const compose = (...fns) => x =>
  fns.reduceRight((acc, fn) => fn(acc), x);

const pipe = (...fns) => x =>
  fns.reduce((acc, fn) => fn(acc), x);

// Example functions
const double = x => x * 2;
const square = x => x * x;
const addOne = x => x + 1;

// Compose (right to left)
const doubleThenSquare = compose(square, double);
console.log(doubleThenSquare(3)); // (3 * 2)^2 = 36

// Pipe (left to right)
const doubleSquareAddOne = pipe(double, square, addOne);
console.log(doubleSquareAddOne(3)); // ((3 * 2)^2) + 1 = 37

// Currying
const curry = (fn) => {
  const arity = fn.length;
  
  return function curried(...args) {
    if (args.length >= arity) {
      return fn(...args);
    }
    return (...moreArgs) => curried(...args, ...moreArgs);
  };
};

// Manual currying
const add = a => b => a + b;
const add5 = add(5);
console.log(add5(3)); // 8

const multiply = a => b => c => a * b * c;
console.log(multiply(2)(3)(4)); // 24

// Curried functions
const curriedMap = curry((fn, arr) => arr.map(fn));
const doubleAll = curriedMap(double);
console.log(doubleAll([1, 2, 3])); // [2, 4, 6]

// Partial application
const partial = (fn, ...args) => (...moreArgs) =>
  fn(...args, ...moreArgs);

const add3Numbers = (a, b, c) => a + b + c;
const add10 = partial(add3Numbers, 10);
console.log(add10(5, 2)); // 17

// Point-free style
const users = [
  { name: 'Alice', age: 30 },
  { name: 'Bob', age: 25 },
  { name: 'Charlie', age: 35 }
];

// Not point-free
const names1 = users.map(user => user.name);

// Point-free
const prop = key => obj => obj[key];
const getName = prop('name');
const names2 = users.map(getName);
```

### Lazy Evaluation

```javascript
// Generators for lazy evaluation
function* range(start, end) {
  for (let i = start; i < end; i++) {
    yield i;
  }
}

// Only computes when needed
const numbers = range(0, 1000000);
for (const n of numbers) {
  if (n > 5) break;
  console.log(n);
}

// Lazy map
function* lazyMap(iterable, fn) {
  for (const item of iterable) {
    yield fn(item);
  }
}

// Lazy filter
function* lazyFilter(iterable, predicate) {
  for (const item of iterable) {
    if (predicate(item)) {
      yield item;
    }
  }
}

// Lazy take
function* take(iterable, n) {
  let count = 0;
  for (const item of iterable) {
    if (count++ >= n) break;
    yield item;
  }
}

// Compose lazy operations
const nums = range(0, 1000000);
const doubled = lazyMap(nums, n => n * 2);
const evens = lazyFilter(doubled, n => n % 4 === 0);
const first10 = take(evens, 10);

console.log([...first10]);

// Infinite sequences
function* fibonacci() {
  let a = 0, b = 1;
  while (true) {
    yield a;
    [a, b] = [b, a + b];
  }
}

const fibs = fibonacci();
console.log([...take(fibs, 10)]);

// Memoization (caching)
function memoize(fn) {
  const cache = new Map();
  
  return function(...args) {
    const key = JSON.stringify(args);
    if (cache.has(key)) {
      return cache.get(key);
    }
    const result = fn(...args);
    cache.set(key, result);
    return result;
  };
}

const fibonacci = memoize(n => {
  if (n <= 1) return n;
  return fibonacci(n - 1) + fibonacci(n - 2);
});
```

## 8. Memory Management

### Garbage Collection

```javascript
// JavaScript uses automatic garbage collection
// Objects are collected when no references exist

function createObjects() {
  let obj1 = { data: new Array(1000000) };
  let obj2 = { data: new Array(1000000) };
  
  // obj1 and obj2 are eligible for GC after function returns
  return null;
}

createObjects();

// Avoiding memory leaks
// 1. Clear timers
const timerId = setTimeout(() => {
  console.log('Hello');
}, 1000);

clearTimeout(timerId);

// 2. Remove event listeners
const button = document.getElementById('btn');
const handler = () => console.log('Clicked');

button.addEventListener('click', handler);
// Later:
button.removeEventListener('click', handler);

// 3. Clear DOM references
let element = document.getElementById('large-element');
element.remove();
element = null; // Clear reference

// 4. Avoid global variables
// BAD:
window.globalData = new Array(1000000);

// GOOD: Use block scope
{
  const data = new Array(1000000);
  // data is eligible for GC after block
}

// 5. Close streams and connections
const fs = require('fs');
const stream = fs.createReadStream('file.txt');
stream.on('end', () => stream.close());

// WeakMap and WeakSet for garbage-collectable references
const cache = new WeakMap();

let obj = { id: 1 };
cache.set(obj, 'some data');

// When obj is no longer referenced, it can be GC'd
obj = null;
```

### Memory Management Patterns

```javascript
// Object pooling
class ObjectPool {
  constructor(factory, reset, initialSize = 10) {
    this.factory = factory;
    this.reset = reset;
    this.pool = [];
    
    for (let i = 0; i < initialSize; i++) {
      this.pool.push(factory());
    }
  }
  
  acquire() {
    return this.pool.length > 0 
      ? this.pool.pop()
      : this.factory();
  }
  
  release(obj) {
    this.reset(obj);
    this.pool.push(obj);
  }
}

// Usage
const vectorPool = new ObjectPool(
  () => ({ x: 0, y: 0 }),
  (v) => { v.x = 0; v.y = 0; }
);

const v1 = vectorPool.acquire();
v1.x = 10;
v1.y = 20;
vectorPool.release(v1);

// String building (avoid concatenation in loops)
// BAD:
let str = '';
for (let i = 0; i < 10000; i++) {
  str += i.toString();
}

// GOOD:
const parts = [];
for (let i = 0; i < 10000; i++) {
  parts.push(i.toString());
}
const str2 = parts.join('');

// Avoiding closures in loops
// BAD:
const functions = [];
for (var i = 0; i < 10; i++) {
  functions.push(function() {
    console.log(i); // All will log 10
  });
}

// GOOD (with let):
const functions2 = [];
for (let i = 0; i < 10; i++) {
  functions2.push(function() {
    console.log(i); // Each logs its own i
  });
}

// GOOD (with IIFE):
const functions3 = [];
for (var i = 0; i < 10; i++) {
  functions3.push((function(i) {
    return function() {
      console.log(i);
    };
  })(i));
}

// Detaching event listeners
class Component {
  constructor() {
    this.handleClick = this.handleClick.bind(this);
  }
  
  mount() {
    document.addEventListener('click', this.handleClick);
  }
  
  unmount() {
    document.removeEventListener('click', this.handleClick);
  }
  
  handleClick() {
    console.log('Clicked');
  }
}
```

### Performance Optimization

```javascript
// Debouncing
function debounce(func, wait) {
  let timeout;
  return function(...args) {
    clearTimeout(timeout);
    timeout = setTimeout(() => func.apply(this, args), wait);
  };
}

// Usage
const handleResize = debounce(() => {
  console.log('Resized');
}, 250);

window.addEventListener('resize', handleResize);

// Throttling
function throttle(func, limit) {
  let inThrottle;
  return function(...args) {
    if (!inThrottle) {
      func.apply(this, args);
      inThrottle = true;
      setTimeout(() => inThrottle = false, limit);
    }
  };
}

// Usage
const handleScroll = throttle(() => {
  console.log('Scrolled');
}, 100);

window.addEventListener('scroll', handleScroll);

// Request animation frame
function animate() {
  // Animation code
  requestAnimationFrame(animate);
}

requestAnimationFrame(animate);

// Batch DOM updates
// BAD:
for (let i = 0; i < 1000; i++) {
  const div = document.createElement('div');
  div.textContent = i;
  document.body.appendChild(div); // Triggers reflow each time
}

// GOOD:
const fragment = document.createDocumentFragment();
for (let i = 0; i < 1000; i++) {
  const div = document.createElement('div');
  div.textContent = i;
  fragment.appendChild(div);
}
document.body.appendChild(fragment); // Single reflow

// Virtual scrolling concept
class VirtualList {
  constructor(items, itemHeight, visibleCount) {
    this.items = items;
    this.itemHeight = itemHeight;
    this.visibleCount = visibleCount;
    this.scrollTop = 0;
  }
  
  getVisibleItems() {
    const start = Math.floor(this.scrollTop / this.itemHeight);
    const end = start + this.visibleCount;
    return this.items.slice(start, end);
  }
  
  onScroll(scrollTop) {
    this.scrollTop = scrollTop;
  }
}
```

## 9. Standard Library

### Console API

```javascript
// Basic logging
console.log('Hello', 'World');
console.info('Information');
console.warn('Warning');
console.error('Error');

// Formatting
console.log('Name: %s, Age: %d', 'Alice', 30);
console.log('Styles: %cBlue %cRed', 'color: blue', 'color: red');

// Objects
const obj = { name: 'Alice', age: 30 };
console.log(obj);
console.dir(obj);
console.table([obj]);

// Grouping
console.group('Group');
console.log('Item 1');
console.log('Item 2');
console.groupEnd();

// Timing
console.time('operation');
// ... code ...
console.timeEnd('operation');

// Assertions
console.assert(1 === 1, 'This won\'t print');
console.assert(1 === 2, 'This will print');

// Counting
console.count('label');
console.count('label');
console.countReset('label');

// Stack trace
console.trace('Trace point');

// Clear
console.clear();
```

### JSON

```javascript
// JSON.stringify
const obj = {
  name: 'Alice',
  age: 30,
  hobbies: ['reading', 'coding']
};

const json = JSON.stringify(obj);
console.log(json);

// Pretty print
const pretty = JSON.stringify(obj, null, 2);
console.log(pretty);

// Replacer function
const filtered = JSON.stringify(obj, (key, value) => {
  if (key === 'age') return undefined;
  return value;
});

// Replacer array
const selected = JSON.stringify(obj, ['name', 'hobbies']);

// JSON.parse
const parsed = JSON.parse(json);

// Reviver function
const withDates = JSON.parse(json, (key, value) => {
  if (key.endsWith('Date')) {
    return new Date(value);
  }
  return value;
});

// toJSON method
class User {
  constructor(name, password) {
    this.name = name;
    this.password = password;
  }
  
  toJSON() {
    return { name: this.name };
  }
}

const user = new User('Alice', 'secret');
console.log(JSON.stringify(user)); // {"name":"Alice"}
```

### Math

```javascript
// Constants
console.log(Math.PI);     // 3.141592653589793
console.log(Math.E);      // 2.718281828459045

// Rounding
console.log(Math.ceil(4.2));   // 5
console.log(Math.floor(4.8));  // 4
console.log(Math.round(4.5));  // 5
console.log(Math.trunc(4.9));  // 4

// Min/Max
console.log(Math.min(1, 2, 3));      // 1
console.log(Math.max(1, 2, 3));      // 3
console.log(Math.min(...[1, 2, 3])); // 1 with spread

// Power and roots
console.log(Math.pow(2, 3));  // 8
console.log(2 ** 3);          // 8 (exponentiation operator)
console.log(Math.sqrt(16));   // 4
console.log(Math.cbrt(27));   // 3

// Absolute and sign
console.log(Math.abs(-5));    // 5
console.log(Math.sign(-5));   // -1
console.log(Math.sign(0));    // 0
console.log(Math.sign(5));    // 1

// Trigonometry (radians)
console.log(Math.sin(Math.PI / 2));  // 1
console.log(Math.cos(0));            // 1
console.log(Math.tan(Math.PI / 4));  // 1
console.log(Math.asin(1));           // π/2
console.log(Math.acos(1));           // 0
console.log(Math.atan(1));           // π/4
console.log(Math.atan2(1, 1));       // π/4

// Logarithms
console.log(Math.log(Math.E));   // 1 (natural log)
console.log(Math.log10(100));    // 2
console.log(Math.log2(8));       // 3

// Random
console.log(Math.random());                    // 0 to 1
console.log(Math.floor(Math.random() * 100)); // 0 to 99

// Random integer in range
function randomInt(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

// Other
console.log(Math.hypot(3, 4));  // 5 (hypotenuse)
```

### Date

```javascript
// Creating dates
const now = new Date();
const specific = new Date('2024-01-15');
const fromComponents = new Date(2024, 0, 15, 14, 30, 0); // Month is 0-indexed
const fromTimestamp = new Date(1705329000000);

// Getting components
console.log(now.getFullYear());      // 2024
console.log(now.getMonth());         // 0-11
console.log(now.getDate());          // 1-31
console.log(now.getDay());           // 0-6 (0 = Sunday)
console.log(now.getHours());         // 0-23
console.log(now.getMinutes());       // 0-59
console.log(now.getSeconds());       // 0-59
console.log(now.getMilliseconds());  // 0-999

// UTC versions
console.log(now.getUTCFullYear());
console.log(now.getUTCMonth());

// Setting components
const date = new Date();
date.setFullYear(2025);
date.setMonth(11); // December
date.setDate(25);
date.setHours(12, 30, 0, 0);

// Timestamps
console.log(now.getTime());          // Milliseconds since epoch
console.log(Date.now());             // Current timestamp
console.log(+now);                   // Convert to timestamp

// String representations
console.log(now.toString());
console.log(now.toISOString());
console.log(now.toLocaleDateString());
console.log(now.toLocaleTimeString());
console.log(now.toUTCString());

// Parsing
console.log(Date.parse('2024-01-15'));

// Comparisons
const date1 = new Date('2024-01-15');
const date2 = new Date('2024-01-20');
console.log(date1 < date2);  // true
console.log(date1.getTime() === date2.getTime()); // false

// Date arithmetic
const tomorrow = new Date();
tomorrow.setDate(tomorrow.getDate() + 1);

const nextWeek = new Date();
nextWeek.setDate(nextWeek.getDate() + 7);

// Difference
const diff = date2 - date1;
const days = diff / (1000 * 60 * 60 * 24);
```

### RegExp

```javascript
// Creating regex
const regex1 = /pattern/flags;
const regex2 = new RegExp('pattern', 'flags');

// Flags
// g - global
// i - case insensitive
// m - multiline
// s - dotAll
// u - unicode
// y - sticky

// Testing
const pattern = /hello/i;
console.log(pattern.test('Hello World')); // true

// Matching
const text = 'The quick brown fox';
const match = text.match(/quick/);
console.log(match); // ['quick', index: 4, input: '...', groups: undefined]

// Global match
const globalMatch = text.match(/\w+/g);
console.log(globalMatch); // ['The', 'quick', 'brown', 'fox']

// Replace
const newText = text.replace(/quick/, 'slow');
const globalReplace = text.replace(/o/g, '0');

// Replace with function
const capitalized = text.replace(/\b\w+\b/g, (match) => {
  return match.charAt(0).toUpperCase() + match.slice(1);
});

// Groups
const datePattern = /(\d{4})-(\d{2})-(\d{2})/;
const dateMatch = '2024-01-15'.match(datePattern);
console.log(dateMatch[1]); // 2024
console.log(dateMatch[2]); // 01
console.log(dateMatch[3]); // 15

// Named groups
const namedPattern = /(?<year>\d{4})-(?<month>\d{2})-(?<day>\d{2})/;
const namedMatch = '2024-01-15'.match(namedPattern);
console.log(namedMatch.groups.year);  // 2024
console.log(namedMatch.groups.month); // 01

// Split
const parts = 'a,b,c,d'.split(/,/);

// Exec
const regex = /\w+/g;
let match;
while ((match = regex.exec(text)) !== null) {
  console.log(match[0], match.index);
}

// Common patterns
const email = /^[\w.-]+@[\w.-]+\.\w+$/;
const phone = /^\d{3}-\d{3}-\d{4}$/;
const url = /^https?:\/\/.+/;
const hex = /^#[0-9A-Fa-f]{6}$/;
```

## 10. Tooling and Ecosystem

### npm and Package Management

```bash
# Initialize project
npm init
npm init -y

# Install packages
npm install package-name
npm install package-name@version
npm install package-name@latest

# Development dependencies
npm install --save-dev eslint
npm install -D typescript

# Global packages
npm install -g typescript
npm install -g nodemon

# Uninstall
npm uninstall package-name

# Update
npm update
npm update package-name

# List packages
npm list
npm list --depth=0

# Outdated packages
npm outdated

# Audit security
npm audit
npm audit fix

# Scripts
npm run script-name
npm start
npm test
npm run build

# Cache
npm cache clean --force
```

### TypeScript Configuration

```json
// tsconfig.json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "commonjs",
    "lib": ["ES2020"],
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "resolveJsonModule": true,
    "declaration": true,
    "declarationMap": true,
    "sourceMap": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noImplicitReturns": true,
    "noFallthroughCasesInSwitch": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules", "**/*.spec.ts"]
}
```

### ES Modules vs CommonJS

```javascript
// CommonJS (Node.js traditional)
// Exporting
module.exports = {
  add: (a, b) => a + b,
  subtract: (a, b) => a - b
};

// or
exports.multiply = (a, b) => a * b;

// Importing
const math = require('./math');
const { add, subtract } = require('./math');

// ES Modules
// Exporting
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;

export default function multiply(a, b) {
  return a * b;
}

// Importing
import multiply, { add, subtract } from './math.js';
import * as math from './math.js';

// Dynamic import
const module = await import('./math.js');

// Re-exporting
export { add, subtract } from './math.js';
export * from './utils.js';
```

### Testing

```javascript
// Jest example
describe('Calculator', () => {
  test('adds two numbers', () => {
    expect(add(2, 3)).toBe(5);
  });
  
  test('subtracts two numbers', () => {
    expect(subtract(5, 3)).toBe(2);
  });
  
  test('throws on division by zero', () => {
    expect(() => divide(10, 0)).toThrow();
  });
});

// Async tests
test('fetches data', async () => {
  const data = await fetchData();
  expect(data).toBeDefined();
});

// Mocking
jest.mock('./api');

test('calls API', () => {
  const mockFetch = jest.fn().mockResolvedValue({ data: 'test' });
  api.fetch = mockFetch;
  
  const result = await fetchData();
  expect(mockFetch).toHaveBeenCalled();
  expect(result.data).toBe('test');
});

// TypeScript testing
import { describe, test, expect } from '@jest/globals';

describe('TypeScript test', () => {
  test('type-safe test', () => {
    const result: number = add(2, 3);
    expect(result).toBe(5);
  });
});
```

### Linting and Formatting

```json
// .eslintrc.json
{
  "extends": ["eslint:recommended"],
  "env": {
    "node": true,
    "es2021": true
  },
  "parserOptions": {
    "ecmaVersion": 12,
    "sourceType": "module"
  },
  "rules": {
    "indent": ["error", 2],
    "quotes": ["error", "single"],
    "semi": ["error", "always"]
  }
}

// .prettierrc
{
  "singleQuote": true,
  "trailingComma": "es5",
  "tabWidth": 2,
  "semi": true
}
```

## 11. Best Practices

### Code Style

```javascript
// Use const/let, not var
const immutable = 'value';
let mutable = 0;

// Descriptive names
const getUserById = (id) => { /* ... */ };
const isValidEmail = (email) => { /* ... */ };

// Arrow functions for short functions
const double = x => x * 2;
const add = (a, b) => a + b;

// Destructuring
const { name, age } = user;
const [first, second] = array;

// Template literals
const message = `Hello, ${name}!`;

// Short-circuit evaluation
const value = input || defaultValue;
const name = user?.name ?? 'Guest';

// Array methods over loops
const doubled = numbers.map(n => n * 2);
const evens = numbers.filter(n => n % 2 === 0);

// Async/await over promises
async function fetchData() {
  const response = await fetch(url);
  const data = await response.json();
  return data;
}

// Early returns
function process(data) {
  if (!data) return null;
  if (data.length === 0) return [];
  
  // Main logic
  return data.map(transform);
}

// Object method shorthand
const obj = {
  method() {
    // ...
  }
};

// Spread for copying
const copy = [...array];
const clone = { ...object };
```

**TypeScript:**
```typescript
// Enable strict mode
// tsconfig.json: "strict": true

// Type everything
function add(a: number, b: number): number {
  return a + b;
}

// Interfaces for objects
interface User {
  id: number;
  name: string;
  email: string;
}

// Type guards
function isString(value: unknown): value is string {
  return typeof value === 'string';
}

// Avoid 'any'
// Use 'unknown' instead
function process(value: unknown) {
  if (typeof value === 'string') {
    return value.toUpperCase();
  }
}

// Use utility types
type PartialUser = Partial<User>;
type ReadonlyUser = Readonly<User>;

// Prefer interfaces over type aliases for objects
interface Point {
  x: number;
  y: number;
}

// Type aliases for unions/intersections
type ID = string | number;
type UserWithTimestamp = User & { timestamp: Date };
```

### Error Handling

```javascript
// Always handle errors
async function fetchData() {
  try {
    const response = await fetch(url);
    if (!response.ok) {
      throw new Error(`HTTP error: ${response.status}`);
    }
    return await response.json();
  } catch (error) {
    console.error('Failed to fetch data:', error);
    throw error;
  }
}

// Custom errors
class ValidationError extends Error {
  constructor(message, field) {
    super(message);
    this.name = 'ValidationError';
    this.field = field;
  }
}

// Error boundaries (React example)
class ErrorBoundary extends React.Component {
  state = { hasError: false };
  
  static getDerivedStateFromError(error) {
    return { hasError: true };
  }
  
  componentDidCatch(error, errorInfo) {
    logError(error, errorInfo);
  }
  
  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong.</h1>;
    }
    return this.props.children;
  }
}
```

### Performance

```javascript
// Avoid unnecessary re-renders (React)
const MemoizedComponent = React.memo(Component);

// Debounce expensive operations
const handleSearch = debounce((query) => {
  // Expensive search operation
}, 300);

// Use Web Workers for heavy computation
const worker = new Worker('worker.js');
worker.postMessage(data);
worker.onmessage = (e) => {
  console.log(e.data);
};

// Lazy loading
const LazyComponent = lazy(() => import('./Component'));

// Code splitting
import(/* webpackChunkName: "feature" */ './feature');

// Optimize loops
// Cache array length
for (let i = 0, len = arr.length; i < len; i++) {
  // ...
}

// Use appropriate data structures
// Map for frequent lookups
const map = new Map();
map.set(key, value); // O(1)

// Set for uniqueness
const set = new Set(array);

// Avoid memory leaks
// Clean up timers
useEffect(() => {
  const id = setInterval(() => {}, 1000);
  return () => clearInterval(id);
}, []);

// Remove event listeners
useEffect(() => {
  const handler = () => {};
  window.addEventListener('resize', handler);
  return () => window.removeEventListener('resize', handler);
}, []);
```

### Security

```javascript
// Sanitize user input
function sanitize(input) {
  return input.replace(/[<>]/g, '');
}

// Use Content Security Policy
// HTTP header: Content-Security-Policy: default-src 'self'

// Avoid eval
// BAD: eval('console.log("hello")');
// GOOD: Use Function constructor or safe alternatives

// Secure API calls
// Use HTTPS
// Include authentication tokens
fetch(url, {
  headers: {
    'Authorization': `Bearer ${token}`,
    'Content-Type': 'application/json'
  }
});

// Validate input
function validateEmail(email) {
  const regex = /^[\w.-]+@[\w.-]+\.\w+$/;
  return regex.test(email);
}

// Use environment variables
const API_KEY = process.env.API_KEY;

// Hash passwords (never store plain text)
const bcrypt = require('bcrypt');
const hash = await bcrypt.hash(password, 10);

// Prevent SQL injection
// Use parameterized queries
const result = await db.query(
  'SELECT * FROM users WHERE id = $1',
  [userId]
);

// Prevent XSS
// Escape user content
// Use frameworks that auto-escape
```

## 12. Conclusion

### Key Takeaways

JavaScript and TypeScript are essential technologies for modern web development:

1. **Ubiquity**: Run everywhere - browsers, servers, mobile, desktop
2. **Modern Features**: ES6+ brings powerful language features
3. **Type Safety**: TypeScript adds compile-time type checking
4. **Async Programming**: First-class support for promises and async/await
5. **Rich Ecosystem**: Millions of packages available via npm
6. **Community**: Largest developer community
7. **Performance**: V8 engine and modern optimizations

### Learning Path

1. **JavaScript Fundamentals**: Master syntax, types, and control flow
2. **ES6+ Features**: Learn modern JavaScript
3. **Async Programming**: Understand promises and async/await
4. **TypeScript**: Add type safety to your code
5. **DOM Manipulation**: Learn browser APIs
6. **Node.js**: Server-side JavaScript
7. **Frameworks**: React, Vue, Angular, etc.
8. **Testing**: Jest, Mocha, Cypress
9. **Build Tools**: Webpack, Vite, esbuild
10. **Best Practices**: Clean code, patterns, performance

### Resources

- **MDN Web Docs**: developer.mozilla.org
- **TypeScript Docs**: typescriptlang.org
- **Node.js Docs**: nodejs.org
- **npm Registry**: npmjs.com
- **Can I Use**: caniuse.com (browser compatibility)

### Next Steps

1. Build real projects
2. Contribute to open source
3. Learn a framework (React, Vue, Angular)
4. Master TypeScript
5. Study design patterns
6. Learn testing and deployment
7. Explore advanced topics (GraphQL, WebAssembly, etc.)

### Complete Example: Todo Application

```typescript
// types.ts
interface Todo {
  id: string;
  title: string;
  completed: boolean;
  createdAt: Date;
}

// todoService.ts
class TodoService {
  private todos: Todo[] = [];
  
  addTodo(title: string): Todo {
    const todo: Todo = {
      id: crypto.randomUUID(),
      title,
      completed: false,
      createdAt: new Date()
    };
    
    this.todos.push(todo);
    return todo;
  }
  
  getTodos(): readonly Todo[] {
    return [...this.todos];
  }
  
  toggleTodo(id: string): void {
    const todo = this.todos.find(t => t.id === id);
    if (todo) {
      todo.completed = !todo.completed;
    }
  }
  
  deleteTodo(id: string): void {
    this.todos = this.todos.filter(t => t.id !== id);
  }
  
  getCompleted(): Todo[] {
    return this.todos.filter(t => t.completed);
  }
  
  getPending(): Todo[] {
    return this.todos.filter(t => !t.completed);
  }
}

// main.ts
const service = new TodoService();

service.addTodo('Learn TypeScript');
service.addTodo('Build an app');
service.addTodo('Deploy to production');

const todos = service.getTodos();
console.log('All todos:', todos);

service.toggleTodo(todos[0].id);

console.log('Completed:', service.getCompleted());
console.log('Pending:', service.getPending());
```

This guide covers the essential aspects of JavaScript and TypeScript programming. Continue practicing, building projects, and staying updated with the evolving ecosystem!
