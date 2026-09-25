# Python Programming Language Proficiency Guide

## 1. Introduction

Python is a high-level, interpreted, general-purpose programming language emphasizing code readability with its notable use of significant indentation. Created by Guido van Rossum and first released in 1991, Python has become one of the most popular programming languages in the world.

### Key Characteristics

- **Simple and readable**: Clear, intuitive syntax
- **Interpreted**: No compilation step needed
- **Dynamically typed**: Types determined at runtime
- **Multi-paradigm**: Supports OOP, functional, and procedural programming
- **Extensive standard library**: "Batteries included" philosophy
- **Cross-platform**: Runs on Windows, macOS, Linux, and more

### Why Learn Python?

- **Versatility**: Web, data science, AI/ML, automation, scripting
- **Beginner-friendly**: Easy to learn and start coding
- **Huge ecosystem**: Rich collection of libraries and frameworks
- **Career opportunities**: High demand in many industries
- **Community**: Large, active, and helpful community
- **Rapid development**: Quick prototyping and development

### Setting Up Python

```bash
# Install Python (download from python.org or use package manager)

# Verify installation
python --version
python3 --version

# Install pip (package manager)
python -m ensurepip --upgrade

# Create virtual environment
python -m venv myenv

# Activate virtual environment
# Windows:
myenv\Scripts\activate
# macOS/Linux:
source myenv/bin/activate

# Install packages
pip install package-name
```

### Hello World

```python
# hello.py
print("Hello, Python!")

# Run with:
# python hello.py
```

## 2. Core Language Mechanics

### Syntax Fundamentals

```python
# Comments
# Single-line comment

"""
Multi-line comment
or documentation string
"""

'''
Also a multi-line
comment/docstring
'''

# Statements don't require semicolons
x = 5
print(x)

# But semicolons are allowed (rarely used)
y = 10; print(y)

# Indentation is significant
if True:
    print("Indented block")
    print("Still in block")
print("Outside block")

# Line continuation
long_sum = 1 + 2 + 3 + \
           4 + 5 + 6

# Or using parentheses (preferred)
long_sum = (1 + 2 + 3 +
            4 + 5 + 6)
```

### Variables and Constants

```python
def variables_demo():
    # Variables (no declaration needed)
    name = "Alice"
    age = 30
    height = 5.6
    is_active = True
    
    # Dynamic typing
    var = 5
    var = "Now a string"
    var = True
    
    # Multiple assignment
    a, b, c = 1, 2, 3
    x = y = z = 0
    
    # Swap variables
    a, b = b, a
    
    # Type hints (Python 3.5+)
    name: str = "Alice"
    age: int = 30
    height: float = 5.6
    is_active: bool = True
    
    # Constants (by convention, use UPPERCASE)
    PI = 3.14159
    MAX_SIZE = 100
    API_KEY = "secret123"
    
    # Delete variables
    x = 10
    del x
    # print(x)  # NameError: name 'x' is not defined
    
    # Global and local scope
    global_var = "global"
    
    def inner():
        local_var = "local"
        print(local_var)
        print(global_var)
    
    inner()
    # print(local_var)  # NameError
```

### Data Types

```python
def data_types_demo():
    # Numbers
    integer = 42
    negative = -10
    big_number = 1_000_000
    
    float_num = 3.14
    scientific = 1.23e5
    
    # Complex numbers
    complex_num = 3 + 4j
    
    # Type conversions
    x = int(3.14)      # 3
    y = float(5)       # 5.0
    z = str(42)        # "42"
    b = bool(1)        # True
    
    # Strings
    single = 'Single quotes'
    double = "Double quotes"
    triple = '''Triple
    quotes for
    multi-line'''
    
    # String formatting
    name = "Alice"
    age = 30
    
    # f-strings (Python 3.6+)
    print(f"{name} is {age} years old")
    print(f"Next year: {age + 1}")
    
    # format() method
    print("{} is {} years old".format(name, age))
    print("{0} is {1} years old".format(name, age))
    print("{name} is {age} years old".format(name=name, age=age))
    
    # % formatting (old style)
    print("%s is %d years old" % (name, age))
    
    # Raw strings
    path = r"C:\Users\name\file.txt"
    
    # String methods
    text = "Hello, World!"
    print(text.upper())
    print(text.lower())
    print(text.capitalize())
    print(text.title())
    print(text.strip())
    print(text.replace("World", "Python"))
    print(text.split(","))
    print(text.startswith("Hello"))
    print(text.endswith("!"))
    print(text.find("World"))
    print(text.count("l"))
    
    # Boolean
    is_true = True
    is_false = False
    
    # Truthy and falsy values
    # Falsy: False, None, 0, 0.0, '', [], {}, ()
    # Truthy: everything else
    
    # None type
    nothing = None
    
    # Checking None
    if nothing is None:
        print("It's None")
    
    # Type checking
    print(type(42))          # <class 'int'>
    print(type("hello"))     # <class 'str'>
    print(isinstance(42, int))  # True
```

### Operators

```python
def operators_demo():
    # Arithmetic
    print(5 + 3)    # 8
    print(5 - 3)    # 2
    print(5 * 3)    # 15
    print(5 / 3)    # 1.6666... (true division)
    print(5 // 3)   # 1 (floor division)
    print(5 % 3)    # 2 (modulo)
    print(5 ** 3)   # 125 (exponentiation)
    
    # Assignment
    x = 10
    x += 5   # x = x + 5
    x -= 3   # x = x - 3
    x *= 2   # x = x * 2
    x /= 4   # x = x / 4
    x //= 2  # x = x // 2
    x %= 3   # x = x % 3
    x **= 2  # x = x ** 2
    
    # Comparison
    print(5 == 3)   # False
    print(5 != 3)   # True
    print(5 > 3)    # True
    print(5 < 3)    # False
    print(5 >= 3)   # True
    print(5 <= 3)   # False
    
    # Logical
    print(True and False)  # False
    print(True or False)   # True
    print(not True)        # False
    
    # Identity
    a = [1, 2, 3]
    b = [1, 2, 3]
    c = a
    print(a == b)   # True (equal values)
    print(a is b)   # False (different objects)
    print(a is c)   # True (same object)
    print(a is not b)  # True
    
    # Membership
    print(3 in [1, 2, 3])     # True
    print(4 not in [1, 2, 3]) # True
    print("a" in "apple")     # True
    
    # Bitwise
    print(5 & 3)    # 1 (AND)
    print(5 | 3)    # 7 (OR)
    print(5 ^ 3)    # 6 (XOR)
    print(~5)       # -6 (NOT)
    print(5 << 1)   # 10 (left shift)
    print(5 >> 1)   # 2 (right shift)
    
    # Walrus operator (Python 3.8+)
    if (n := len([1, 2, 3])) > 2:
        print(f"Length is {n}")
```

### Type Hints and Annotations

```python
from typing import List, Dict, Tuple, Optional, Union, Any

def type_hints_demo():
    # Basic type hints
    name: str = "Alice"
    age: int = 30
    height: float = 5.6
    is_active: bool = True
    
    # Collection types
    numbers: List[int] = [1, 2, 3, 4, 5]
    names: List[str] = ["Alice", "Bob", "Charlie"]
    
    # Dictionary
    user: Dict[str, int] = {"Alice": 30, "Bob": 25}
    
    # Tuple
    point: Tuple[int, int] = (10, 20)
    
    # Optional (can be None)
    middle_name: Optional[str] = None
    
    # Union (multiple possible types)
    id_value: Union[int, str] = "ABC123"
    
    # Any (any type)
    data: Any = "can be anything"
    
    # Function annotations
    def greet(name: str) -> str:
        return f"Hello, {name}!"
    
    def add(a: int, b: int) -> int:
        return a + b
    
    def process_items(items: List[str]) -> Dict[str, int]:
        return {item: len(item) for item in items}
    
    # Optional return
    def find_user(user_id: int) -> Optional[str]:
        if user_id > 0:
            return f"User {user_id}"
        return None
```

## 3. Control Flow

### Conditional Statements

```python
def conditionals_demo():
    age = 20
    
    # if-elif-else
    if age < 18:
        print("Minor")
    elif age < 65:
        print("Adult")
    else:
        print("Senior")
    
    # One-line if
    status = "Adult" if age >= 18 else "Minor"
    
    # Nested conditions
    score = 85
    if score >= 90:
        grade = "A"
    elif score >= 80:
        if score >= 85:
            grade = "B+"
        else:
            grade = "B"
    else:
        grade = "C"
    
    # Multiple conditions
    x = 5
    if 0 < x < 10:
        print("Single digit")
    
    # Any and all
    numbers = [2, 4, 6, 8]
    if all(n % 2 == 0 for n in numbers):
        print("All even")
    
    if any(n > 5 for n in numbers):
        print("At least one greater than 5")
    
    # Match-case (Python 3.10+)
    def http_status(status):
        match status:
            case 200:
                return "OK"
            case 404:
                return "Not Found"
            case 500:
                return "Server Error"
            case _:
                return "Unknown"
    
    # Pattern matching with structures
    def process_point(point):
        match point:
            case (0, 0):
                return "Origin"
            case (0, y):
                return f"Y-axis at {y}"
            case (x, 0):
                return f"X-axis at {x}"
            case (x, y):
                return f"Point at ({x}, {y})"
```

### Loops

```python
def loops_demo():
    # For loop with range
    for i in range(5):
        print(i)  # 0, 1, 2, 3, 4
    
    for i in range(1, 6):
        print(i)  # 1, 2, 3, 4, 5
    
    for i in range(0, 10, 2):
        print(i)  # 0, 2, 4, 6, 8
    
    # For loop with collections
    fruits = ["apple", "banana", "orange"]
    for fruit in fruits:
        print(fruit)
    
    # For loop with enumerate
    for index, fruit in enumerate(fruits):
        print(f"{index}: {fruit}")
    
    for index, fruit in enumerate(fruits, start=1):
        print(f"{index}: {fruit}")
    
    # For loop with zip
    names = ["Alice", "Bob", "Charlie"]
    ages = [30, 25, 35]
    for name, age in zip(names, ages):
        print(f"{name} is {age}")
    
    # While loop
    count = 0
    while count < 5:
        print(count)
        count += 1
    
    # Break and continue
    for i in range(10):
        if i == 3:
            continue  # Skip 3
        if i == 7:
            break     # Stop at 7
        print(i)
    
    # Else with loops
    for i in range(5):
        if i == 10:
            break
    else:
        print("Loop completed without break")
    
    # Nested loops
    for i in range(3):
        for j in range(3):
            print(f"({i}, {j})")
    
    # List comprehension (loop alternative)
    squares = [x**2 for x in range(10)]
    evens = [x for x in range(20) if x % 2 == 0]
    
    # Dictionary comprehension
    square_dict = {x: x**2 for x in range(5)}
    
    # Set comprehension
    unique_lengths = {len(word) for word in ["apple", "banana", "cherry"]}
```

### Exception Handling

```python
def exception_handling_demo():
    # Basic try-except
    try:
        result = 10 / 0
    except ZeroDivisionError:
        print("Cannot divide by zero")
    
    # Multiple except blocks
    try:
        value = int("abc")
    except ValueError:
        print("Invalid integer")
    except TypeError:
        print("Type error")
    except Exception as e:
        print(f"General error: {e}")
    
    # Try-except-else-finally
    try:
        file = open("data.txt", "r")
        data = file.read()
    except FileNotFoundError:
        print("File not found")
    else:
        print("File read successfully")
    finally:
        print("Cleanup code runs regardless")
        # file.close()
    
    # Raising exceptions
    def divide(a, b):
        if b == 0:
            raise ValueError("Cannot divide by zero")
        return a / b
    
    # Custom exceptions
    class ValidationError(Exception):
        def __init__(self, message, field):
            super().__init__(message)
            self.field = field
    
    def validate_age(age):
        if age < 0:
            raise ValidationError("Age cannot be negative", "age")
    
    try:
        validate_age(-5)
    except ValidationError as e:
        print(f"Validation error in {e.field}: {e}")
    
    # Context managers (with statement)
    with open("data.txt", "r") as file:
        data = file.read()
        # File automatically closed
    
    # Assert
    age = 20
    assert age >= 0, "Age must be non-negative"
    
    # Try-except as expression
    try:
        number = int("42")
    except ValueError:
        number = -1
    
    # Catching all exceptions
    try:
        # risky operation
        pass
    except Exception as e:
        print(f"Error: {e}")
```

## 4. Functions and Code Organization

### Function Basics

```python
# Basic function
def greet(name):
    print(f"Hello, {name}!")

# Function with return
def add(a, b):
    return a + b

# Multiple return values
def get_stats(numbers):
    return min(numbers), max(numbers), sum(numbers)

# Default parameters
def power(base, exponent=2):
    return base ** exponent

# Keyword arguments
def create_user(name, age, email="", phone=None):
    print(f"Name: {name}")
    print(f"Age: {age}")
    if email:
        print(f"Email: {email}")
    if phone:
        print(f"Phone: {phone}")

def functions_demo():
    # Call functions
    greet("Alice")
    result = add(5, 3)
    
    # Multiple return values
    min_val, max_val, total = get_stats([1, 2, 3, 4, 5])
    
    # Default parameters
    print(power(2))      # 4
    print(power(2, 3))   # 8
    
    # Keyword arguments
    create_user("Alice", 30)
    create_user(name="Bob", age=25, email="bob@example.com")
    create_user("Charlie", 35, phone="555-1234")
    
    # Mix positional and keyword
    create_user("David", age=40, email="david@example.com")

# *args (variable positional arguments)
def sum_all(*numbers):
    return sum(numbers)

print(sum_all(1, 2, 3, 4, 5))

# **kwargs (variable keyword arguments)
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_info(name="Alice", age=30, city="NYC")

# Combining args and kwargs
def complex_function(required, *args, optional=None, **kwargs):
    print(f"Required: {required}")
    print(f"Args: {args}")
    print(f"Optional: {optional}")
    print(f"Kwargs: {kwargs}")

# Lambda functions (anonymous)
square = lambda x: x ** 2
add = lambda a, b: a + b
is_even = lambda x: x % 2 == 0

# Type hints with functions
def typed_add(a: int, b: int) -> int:
    return a + b

def process_list(items: list[str]) -> dict[str, int]:
    return {item: len(item) for item in items}

# Docstrings
def calculate_area(width, height):
    """
    Calculate the area of a rectangle.
    
    Args:
        width (float): The width of the rectangle
        height (float): The height of the rectangle
    
    Returns:
        float: The area of the rectangle
    
    Example:
        >>> calculate_area(5, 3)
        15
    """
    return width * height
```

### Higher-Order Functions

```python
def higher_order_demo():
    # Function as parameter
    def apply_operation(a, b, operation):
        return operation(a, b)
    
    result = apply_operation(5, 3, lambda a, b: a + b)
    print(result)  # 8
    
    # Function returning function
    def make_multiplier(factor):
        def multiplier(x):
            return x * factor
        return multiplier
    
    double = make_multiplier(2)
    triple = make_multiplier(3)
    print(double(5))  # 10
    print(triple(5))  # 15
    
    # Map, filter, reduce
    numbers = [1, 2, 3, 4, 5]
    
    # Map
    doubled = list(map(lambda x: x * 2, numbers))
    squared = list(map(lambda x: x ** 2, numbers))
    
    # Filter
    evens = list(filter(lambda x: x % 2 == 0, numbers))
    greater_than_2 = list(filter(lambda x: x > 2, numbers))
    
    # Reduce
    from functools import reduce
    sum_all = reduce(lambda a, b: a + b, numbers)
    product = reduce(lambda a, b: a * b, numbers)
    
    # List comprehension (preferred over map/filter)
    doubled = [x * 2 for x in numbers]
    evens = [x for x in numbers if x % 2 == 0]
```

### Decorators

```python
# Basic decorator
def my_decorator(func):
    def wrapper():
        print("Before function")
        func()
        print("After function")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

# Decorator with arguments
def repeat(times):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(times):
                func(*args, **kwargs)
        return wrapper
    return decorator

@repeat(3)
def greet(name):
    print(f"Hello, {name}!")

# Decorator preserving metadata
from functools import wraps

def my_decorator(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        print("Before")
        result = func(*args, **kwargs)
        print("After")
        return result
    return wrapper

# Class decorator
def singleton(cls):
    instances = {}
    def get_instance(*args, **kwargs):
        if cls not in instances:
            instances[cls] = cls(*args, **kwargs)
        return instances[cls]
    return get_instance

@singleton
class Database:
    pass

# Built-in decorators
class MyClass:
    _value = 0
    
    @property
    def value(self):
        return self._value
    
    @value.setter
    def value(self, val):
        if val >= 0:
            self._value = val
    
    @staticmethod
    def static_method():
        print("Static method")
    
    @classmethod
    def class_method(cls):
        print(f"Class method of {cls}")
```

### Generators and Iterators

```python
# Generator function
def count_up_to(max):
    count = 1
    while count <= max:
        yield count
        count += 1

for num in count_up_to(5):
    print(num)

# Generator expression
squares = (x**2 for x in range(10))
for square in squares:
    print(square)

# Infinite generator
def fibonacci():
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a + b

# Iterator protocol
class Counter:
    def __init__(self, max):
        self.max = max
        self.current = 0
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.current >= self.max:
            raise StopIteration
        self.current += 1
        return self.current

# Using itertools
from itertools import islice, count, cycle, repeat

# Take first 10 from infinite sequence
fib = fibonacci()
first_10 = list(islice(fib, 10))

# Infinite counter
for i in islice(count(start=10, step=2), 5):
    print(i)  # 10, 12, 14, 16, 18

# Cycle through sequence
for item in islice(cycle(['a', 'b', 'c']), 7):
    print(item)  # a, b, c, a, b, c, a
```

### Async/Await

```python
import asyncio

# Async function
async def fetch_data(id):
    print(f"Fetching {id}...")
    await asyncio.sleep(1)  # Simulate I/O
    return f"Data {id}"

# Async main
async def main():
    # Sequential
    data1 = await fetch_data(1)
    data2 = await fetch_data(2)
    print(data1, data2)
    
    # Parallel
    results = await asyncio.gather(
        fetch_data(1),
        fetch_data(2),
        fetch_data(3)
    )
    print(results)

# Run async code
# asyncio.run(main())

# Async generator
async def async_counter(max):
    for i in range(max):
        await asyncio.sleep(0.1)
        yield i

# Async comprehension
async def async_comprehension_demo():
    result = [i async for i in async_counter(5)]
    print(result)
```

## 5. Data Structures

### Lists

```python
def lists_demo():
    # Creating lists
    numbers = [1, 2, 3, 4, 5]
    mixed = [1, "two", 3.0, True]
    empty = []
    filled = [0] * 5
    
    # List comprehension
    squares = [x**2 for x in range(10)]
    evens = [x for x in range(20) if x % 2 == 0]
    
    # Nested comprehension
    matrix = [[i*j for j in range(3)] for i in range(3)]
    
    # Access
    print(numbers[0])       # First element
    print(numbers[-1])      # Last element
    print(numbers[1:4])     # Slice [1, 2, 3]
    print(numbers[:3])      # First 3
    print(numbers[2:])      # From index 2
    print(numbers[::2])     # Every 2nd element
    print(numbers[::-1])    # Reversed
    
    # Modify
    numbers[0] = 10
    numbers[1:3] = [20, 30]
    
    # Add elements
    numbers.append(6)
    numbers.insert(0, 0)
    numbers.extend([7, 8, 9])
    
    # Remove elements
    numbers.remove(10)      # Remove first occurrence
    popped = numbers.pop()  # Remove and return last
    popped = numbers.pop(0) # Remove at index
    del numbers[0]
    numbers.clear()
    
    # Searching
    numbers = [1, 2, 3, 4, 5, 3]
    print(3 in numbers)
    print(numbers.index(3))
    print(numbers.count(3))
    
    # Sorting
    unsorted = [3, 1, 4, 1, 5, 9, 2, 6]
    sorted_list = sorted(unsorted)
    unsorted.sort()
    unsorted.sort(reverse=True)
    
    words = ["banana", "apple", "cherry"]
    words.sort(key=len)
    
    # Reversing
    numbers.reverse()
    reversed_list = list(reversed(numbers))
    
    # Copying
    copy1 = numbers.copy()
    copy2 = numbers[:]
    copy3 = list(numbers)
    
    # List operations
    list1 = [1, 2, 3]
    list2 = [4, 5, 6]
    combined = list1 + list2
    repeated = list1 * 3
    
    # Unpacking
    first, *middle, last = [1, 2, 3, 4, 5]
    print(first, middle, last)  # 1 [2, 3, 4] 5
    
    # zip
    names = ["Alice", "Bob", "Charlie"]
    ages = [30, 25, 35]
    zipped = list(zip(names, ages))
    
    # enumerate
    for index, value in enumerate(numbers):
        print(f"{index}: {value}")
    
    # any and all
    print(any(x > 3 for x in numbers))
    print(all(x > 0 for x in numbers))
    
    # sum, min, max
    print(sum(numbers))
    print(min(numbers))
    print(max(numbers))
```

### Tuples

```python
def tuples_demo():
    # Creating tuples
    point = (10, 20)
    person = ("Alice", 30, "NYC")
    single = (42,)  # Note the comma
    empty = ()
    
    # Tuple unpacking
    x, y = point
    name, age, city = person
    
    # Access (immutable)
    print(point[0])
    print(point[-1])
    print(person[1:3])
    
    # Can't modify
    # point[0] = 5  # TypeError
    
    # Tuple methods
    numbers = (1, 2, 3, 2, 4, 2)
    print(numbers.count(2))
    print(numbers.index(3))
    
    # Named tuples
    from collections import namedtuple
    
    Point = namedtuple('Point', ['x', 'y'])
    p = Point(10, 20)
    print(p.x, p.y)
    print(p[0], p[1])
    
    Person = namedtuple('Person', ['name', 'age'])
    person = Person(name="Alice", age=30)
    print(person.name, person.age)
```

### Sets

```python
def sets_demo():
    # Creating sets
    numbers = {1, 2, 3, 4, 5}
    mixed = {1, "two", 3.0}
    empty = set()
    from_list = set([1, 2, 2, 3, 3, 3])  # {1, 2, 3}
    
    # Set comprehension
    squares = {x**2 for x in range(10)}
    
    # Add and remove
    numbers.add(6)
    numbers.remove(1)    # Raises KeyError if not found
    numbers.discard(10)  # No error if not found
    popped = numbers.pop()
    numbers.clear()
    
    # Set operations
    a = {1, 2, 3, 4}
    b = {3, 4, 5, 6}
    
    # Union
    print(a | b)
    print(a.union(b))
    
    # Intersection
    print(a & b)
    print(a.intersection(b))
    
    # Difference
    print(a - b)
    print(a.difference(b))
    
    # Symmetric difference
    print(a ^ b)
    print(a.symmetric_difference(b))
    
    # Subset and superset
    c = {1, 2}
    print(c < a)          # Proper subset
    print(c <= a)         # Subset
    print(a > c)          # Proper superset
    print(a >= c)         # Superset
    
    # Membership
    print(3 in a)
    print(10 not in a)
    
    # Remove duplicates from list
    numbers = [1, 2, 2, 3, 3, 3, 4, 5, 5]
    unique = list(set(numbers))
    
    # Frozen set (immutable)
    frozen = frozenset([1, 2, 3])
    # frozen.add(4)  # AttributeError
```

### Dictionaries

```python
def dicts_demo():
    # Creating dictionaries
    person = {"name": "Alice", "age": 30, "city": "NYC"}
    empty = {}
    empty2 = dict()
    from_pairs = dict([("a", 1), ("b", 2)])
    
    # Dict comprehension
    squares = {x: x**2 for x in range(5)}
    
    # Access
    print(person["name"])
    print(person.get("age"))
    print(person.get("email", "none"))  # Default value
    
    # Modify
    person["age"] = 31
    person["email"] = "alice@example.com"
    
    # Delete
    del person["city"]
    popped = person.pop("email")
    person.popitem()  # Remove and return arbitrary item
    
    # Keys, values, items
    print(person.keys())
    print(person.values())
    print(person.items())
    
    # Iteration
    for key in person:
        print(key, person[key])
    
    for key, value in person.items():
        print(f"{key}: {value}")
    
    # Membership
    print("name" in person)
    print("email" not in person)
    
    # Update
    person.update({"age": 32, "phone": "555-1234"})
    person.update(age=33, city="Boston")
    
    # Merge dictionaries (Python 3.9+)
    dict1 = {"a": 1, "b": 2}
    dict2 = {"b": 3, "c": 4}
    merged = dict1 | dict2
    
    # setdefault
    person.setdefault("country", "USA")
    
    # defaultdict
    from collections import defaultdict
    
    word_count = defaultdict(int)
    for word in ["apple", "banana", "apple"]:
        word_count[word] += 1
    
    # OrderedDict (maintains insertion order)
    from collections import OrderedDict
    ordered = OrderedDict()
    ordered["a"] = 1
    ordered["c"] = 3
    ordered["b"] = 2
    
    # Counter
    from collections import Counter
    
    words = ["apple", "banana", "apple", "cherry", "banana", "apple"]
    counter = Counter(words)
    print(counter.most_common(2))
```

### Collections Module

```python
from collections import deque, ChainMap, UserDict

def collections_demo():
    # deque (double-ended queue)
    d = deque([1, 2, 3])
    d.append(4)         # Add to right
    d.appendleft(0)     # Add to left
    d.pop()             # Remove from right
    d.popleft()         # Remove from left
    d.extend([5, 6])    # Extend right
    d.extendleft([-2, -1])  # Extend left
    d.rotate(1)         # Rotate right
    d.rotate(-1)        # Rotate left
    
    # ChainMap
    dict1 = {"a": 1, "b": 2}
    dict2 = {"b": 3, "c": 4}
    chain = ChainMap(dict1, dict2)
    print(chain["a"])   # 1 (from dict1)
    print(chain["b"])   # 2 (from dict1, not dict2)
    print(chain["c"])   # 4 (from dict2)
    
    # UserDict (for subclassing)
    class MyDict(UserDict):
        def __setitem__(self, key, value):
            if isinstance(value, int):
                super().__setitem__(key, value)
```

## 6. Object-Oriented Programming

### Classes and Objects

```python
# Basic class
class Person:
    # Class variable
    species = "Homo sapiens"
    
    # Constructor
    def __init__(self, name, age):
        # Instance variables
        self.name = name
        self.age = age
    
    # Instance method
    def greet(self):
        print(f"Hello, I'm {self.name}")
    
    def have_birthday(self):
        self.age += 1
    
    # String representation
    def __str__(self):
        return f"Person(name={self.name}, age={self.age})"
    
    def __repr__(self):
        return f"Person('{self.name}', {self.age})"

# Creating objects
person = Person("Alice", 30)
person.greet()
print(person)

# Properties
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height
    
    @property
    def area(self):
        return self.width * self.height
    
    @property
    def perimeter(self):
        return 2 * (self.width + self.height)

rect = Rectangle(5, 3)
print(rect.area)

# Getter and setter
class Temperature:
    def __init__(self, celsius=0):
        self._celsius = celsius
    
    @property
    def celsius(self):
        return self._celsius
    
    @celsius.setter
    def celsius(self, value):
        if value < -273.15:
            raise ValueError("Temperature below absolute zero")
        self._celsius = value
    
    @property
    def fahrenheit(self):
        return self._celsius * 9/5 + 32
    
    @fahrenheit.setter
    def fahrenheit(self, value):
        self.celsius = (value - 32) * 5/9

# Private and protected
class BankAccount:
    def __init__(self, account_number):
        self.__account_number = account_number  # Private
        self._balance = 0  # Protected (by convention)
    
    def deposit(self, amount):
        if amount > 0:
            self._balance += amount
    
    def get_balance(self):
        return self._balance

# Static and class methods
class MathUtils:
    @staticmethod
    def add(a, b):
        return a + b
    
    @classmethod
    def create_from_string(cls, string):
        # Factory method
        return cls()

# Dataclasses (Python 3.7+)
from dataclasses import dataclass, field

@dataclass
class User:
    name: str
    age: int
    email: str = ""
    friends: list = field(default_factory=list)
    
    def greet(self):
        return f"Hello, I'm {self.name}"

user = User("Alice", 30)
print(user)
```

### Inheritance

```python
# Base class
class Animal:
    def __init__(self, name):
        self.name = name
    
    def make_sound(self):
        print("Some generic sound")
    
    def eat(self):
        print(f"{self.name} is eating")

# Derived class
class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name)
        self.breed = breed
    
    def make_sound(self):
        print(f"{self.name} barks: Woof!")
    
    def fetch(self):
        print(f"{self.name} is fetching")

class Cat(Animal):
    def make_sound(self):
        print(f"{self.name} meows")
    
    def scratch(self):
        print(f"{self.name} is scratching")

# Multi-level inheritance
class Puppy(Dog):
    def __init__(self, name, breed):
        super().__init__(name, breed)
        self.age = 0
    
    def play(self):
        print(f"{self.name} is playing")

# Multiple inheritance
class Flying:
    def fly(self):
        print("Flying")

class Swimming:
    def swim(self):
        print("Swimming")

class Duck(Animal, Flying, Swimming):
    def make_sound(self):
        print("Quack!")

# Method Resolution Order (MRO)
print(Duck.mro())

# isinstance and issubclass
dog = Dog("Buddy", "Golden Retriever")
print(isinstance(dog, Dog))      # True
print(isinstance(dog, Animal))   # True
print(issubclass(Dog, Animal))   # True
```

### Abstract Classes and Interfaces

```python
from abc import ABC, abstractmethod

# Abstract class
class Shape(ABC):
    @abstractmethod
    def area(self):
        pass
    
    @abstractmethod
    def perimeter(self):
        pass
    
    def display(self):
        print(f"Area: {self.area()}")
        print(f"Perimeter: {self.perimeter()}")

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius
    
    def area(self):
        return 3.14159 * self.radius ** 2
    
    def perimeter(self):
        return 2 * 3.14159 * self.radius

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height
    
    def area(self):
        return self.width * self.height
    
    def perimeter(self):
        return 2 * (self.width + self.height)

# Interface (by convention)
class Drawable(ABC):
    @abstractmethod
    def draw(self):
        pass

class Movable(ABC):
    @abstractmethod
    def move(self, x, y):
        pass

class GameObject(Drawable, Movable):
    def __init__(self, x=0, y=0):
        self.x = x
        self.y = y
    
    def draw(self):
        print(f"Drawing at ({self.x}, {self.y})")
    
    def move(self, x, y):
        self.x = x
        self.y = y
```

### Magic Methods (Dunder Methods)

```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    # String representation
    def __str__(self):
        return f"Vector({self.x}, {self.y})"
    
    def __repr__(self):
        return f"Vector({self.x}, {self.y})"
    
    # Arithmetic operations
    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)
    
    def __sub__(self, other):
        return Vector(self.x - other.x, self.y - other.y)
    
    def __mul__(self, scalar):
        return Vector(self.x * scalar, self.y * scalar)
    
    # Comparison
    def __eq__(self, other):
        return self.x == other.x and self.y == other.y
    
    def __lt__(self, other):
        return self.magnitude() < other.magnitude()
    
    # Length
    def __len__(self):
        return 2
    
    # Indexing
    def __getitem__(self, index):
        if index == 0:
            return self.x
        elif index == 1:
            return self.y
        raise IndexError("Vector index out of range")
    
    # Container methods
    def __contains__(self, value):
        return value == self.x or value == self.y
    
    # Callable
    def __call__(self):
        return self.magnitude()
    
    def magnitude(self):
        return (self.x**2 + self.y**2) ** 0.5

# Context manager
class FileManager:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode
        self.file = None
    
    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file
    
    def __exit__(self, exc_type, exc_val, exc_tb):
        if self.file:
            self.file.close()
        return False

# Usage
with FileManager("data.txt", "w") as f:
    f.write("Hello, World!")
```

### Design Patterns

```python
# Singleton
class Singleton:
    _instance = None
    
    def __new__(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance

# Factory
class ShapeFactory:
    @staticmethod
    def create_shape(shape_type, *args):
        if shape_type == "circle":
            return Circle(*args)
        elif shape_type == "rectangle":
            return Rectangle(*args)
        raise ValueError(f"Unknown shape type: {shape_type}")

# Builder
class UserBuilder:
    def __init__(self):
        self.user = {}
    
    def set_name(self, name):
        self.user['name'] = name
        return self
    
    def set_age(self, age):
        self.user['age'] = age
        return self
    
    def set_email(self, email):
        self.user['email'] = email
        return self
    
    def build(self):
        return self.user

user = (UserBuilder()
        .set_name("Alice")
        .set_age(30)
        .set_email("alice@example.com")
        .build())

# Observer
class Subject:
    def __init__(self):
        self._observers = []
    
    def attach(self, observer):
        self._observers.append(observer)
    
    def detach(self, observer):
        self._observers.remove(observer)
    
    def notify(self, data):
        for observer in self._observers:
            observer.update(data)

class Observer:
    def update(self, data):
        print(f"Received: {data}")
```

## 7. Functional Programming Concepts

### Map, Filter, Reduce

```python
from functools import reduce

def functional_demo():
    numbers = [1, 2, 3, 4, 5]
    
    # Map
    doubled = list(map(lambda x: x * 2, numbers))
    squared = list(map(lambda x: x ** 2, numbers))
    
    # Filter
    evens = list(filter(lambda x: x % 2 == 0, numbers))
    greater_than_2 = list(filter(lambda x: x > 2, numbers))
    
    # Reduce
    sum_all = reduce(lambda a, b: a + b, numbers)
    product = reduce(lambda a, b: a * b, numbers)
    
    # List comprehension (preferred)
    doubled = [x * 2 for x in numbers]
    evens = [x for x in numbers if x % 2 == 0]
    
    # Multiple operations
    result = [x ** 2 for x in numbers if x % 2 == 0]
    
    # any and all
    has_even = any(x % 2 == 0 for x in numbers)
    all_positive = all(x > 0 for x in numbers)
```

### Closures and Decorators

```python
# Closure
def make_counter():
    count = 0
    
    def counter():
        nonlocal count
        count += 1
        return count
    
    return counter

counter = make_counter()
print(counter())  # 1
print(counter())  # 2

# Decorator pattern
from functools import wraps

def timing_decorator(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        import time
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__} took {end - start:.4f} seconds")
        return result
    return wrapper

@timing_decorator
def slow_function():
    import time
    time.sleep(1)
    return "Done"

# Memoization
def memoize(func):
    cache = {}
    @wraps(func)
    def wrapper(*args):
        if args not in cache:
            cache[args] = func(*args)
        return cache[args]
    return wrapper

@memoize
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

# functools.lru_cache
from functools import lru_cache

@lru_cache(maxsize=128)
def fibonacci_cached(n):
    if n <= 1:
        return n
    return fibonacci_cached(n-1) + fibonacci_cached(n-2)
```

### Partial Functions and Composition

```python
from functools import partial

def partial_demo():
    # Partial application
    def power(base, exponent):
        return base ** exponent
    
    square = partial(power, exponent=2)
    cube = partial(power, exponent=3)
    
    print(square(5))  # 25
    print(cube(5))    # 125
    
    # Function composition
    def compose(*functions):
        def inner(arg):
            for func in reversed(functions):
                arg = func(arg)
            return arg
        return inner
    
    def add_one(x):
        return x + 1
    
    def double(x):
        return x * 2
    
    def square(x):
        return x ** 2
    
    composed = compose(square, double, add_one)
    print(composed(3))  # ((3 + 1) * 2) ** 2 = 64
```

### Pure Functions and Immutability

```python
# Pure function (no side effects)
def pure_add(a, b):
    return a + b

def pure_factorial(n):
    if n <= 1:
        return 1
    return n * pure_factorial(n - 1)

# Avoiding mutations
def add_item(lst, item):
    # Bad: mutates original
    # lst.append(item)
    # return lst
    
    # Good: returns new list
    return lst + [item]

def update_dict(d, key, value):
    # Good: returns new dict
    return {**d, key: value}

# Using tuples for immutable data
point = (10, 20)
# point[0] = 5  # TypeError

# Using frozenset for immutable set
frozen = frozenset([1, 2, 3])
# frozen.add(4)  # AttributeError

# Immutable data with dataclasses
from dataclasses import dataclass

@dataclass(frozen=True)
class Point:
    x: int
    y: int
```

## 8. Memory Management

### Reference Counting and Garbage Collection

```python
import sys
import gc

def memory_demo():
    # Reference counting
    a = [1, 2, 3]
    print(sys.getrefcount(a))  # > 1
    
    b = a  # New reference
    print(sys.getrefcount(a))  # Increased
    
    del b  # Remove reference
    print(sys.getrefcount(a))  # Decreased
    
    # Garbage collection
    gc.collect()  # Force garbage collection
    
    # Check if GC is enabled
    print(gc.isenabled())
    
    # Disable/enable GC
    gc.disable()
    gc.enable()

# Memory leaks (circular references)
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None

# Circular reference
node1 = Node(1)
node2 = Node(2)
node1.next = node2
node2.next = node1  # Circular

# Use weakref to avoid cycles
import weakref

class Node:
    def __init__(self, value):
        self.value = value
        self._next = None
    
    @property
    def next(self):
        return self._next() if self._next else None
    
    @next.setter
    def next(self, node):
        self._next = weakref.ref(node) if node else None

# Context managers for resource management
with open("file.txt", "r") as f:
    data = f.read()
    # File automatically closed
```

### Memory Optimization

```python
# Use generators instead of lists
def large_range(n):
    # Bad: creates list in memory
    # return list(range(n))
    
    # Good: generator
    return (i for i in range(n))

# Slots to reduce memory
class WithoutSlots:
    def __init__(self, x, y):
        self.x = x
        self.y = y

class WithSlots:
    __slots__ = ['x', 'y']
    
    def __init__(self, x, y):
        self.x = x
        self.y = y

# String interning
a = "hello"
b = "hello"
print(a is b)  # True (interned)

# Avoid global variables
# Bad: holds reference forever
global_data = [0] * 1000000

# Good: use local scope
def process():
    local_data = [0] * 1000000
    # Process data
    # data freed when function returns

# Object pools
class ObjectPool:
    def __init__(self, factory):
        self.factory = factory
        self.pool = []
    
    def acquire(self):
        if self.pool:
            return self.pool.pop()
        return self.factory()
    
    def release(self, obj):
        self.pool.append(obj)
```

## 9. Standard Library

### Built-in Functions

```python
def builtin_demo():
    # Type conversions
    int("42")
    float("3.14")
    str(42)
    bool(1)
    list("abc")
    tuple([1, 2, 3])
    set([1, 2, 2, 3])
    dict([("a", 1), ("b", 2)])
    
    # Math
    abs(-5)
    pow(2, 3)
    round(3.14159, 2)
    divmod(10, 3)
    
    # Sequences
    len([1, 2, 3])
    min([1, 2, 3])
    max([1, 2, 3])
    sum([1, 2, 3])
    sorted([3, 1, 2])
    reversed([1, 2, 3])
    enumerate(["a", "b", "c"])
    zip([1, 2], ["a", "b"])
    
    # Functional
    map(lambda x: x*2, [1, 2, 3])
    filter(lambda x: x%2==0, [1,2,3,4])
    any([False, True, False])
    all([True, True, False])
    
    # Object
    isinstance(42, int)
    type(42)
    id(object)
    hasattr(obj, "attribute")
    getattr(obj, "attribute", default)
    setattr(obj, "attribute", value)
    delattr(obj, "attribute")
    
    # Input/Output
    print("Hello")
    input("Enter name: ")
    
    # File operations
    open("file.txt", "r")
    
    # Other
    range(10)
    help(function)
    dir(object)
    vars(object)
```

### String Operations

```python
import string

def string_demo():
    # String constants
    print(string.ascii_letters)
    print(string.ascii_lowercase)
    print(string.ascii_uppercase)
    print(string.digits)
    print(string.punctuation)
    
    # String methods
    s = "Hello, World!"
    s.upper()
    s.lower()
    s.capitalize()
    s.title()
    s.swapcase()
    s.strip()
    s.lstrip()
    s.rstrip()
    s.replace("World", "Python")
    s.split(",")
    " ".join(["a", "b", "c"])
    s.startswith("Hello")
    s.endswith("!")
    s.find("World")
    s.index("World")
    s.count("l")
    s.isalpha()
    s.isdigit()
    s.isalnum()
    s.isspace()
    s.islower()
    s.isupper()
    s.center(20)
    s.ljust(20)
    s.rjust(20)
    s.zfill(20)
```

### File I/O

```python
def file_io_demo():
    # Writing
    with open("data.txt", "w") as f:
        f.write("Hello, World!\n")
        f.write("Second line\n")
        f.writelines(["Line 3\n", "Line 4\n"])
    
    # Reading
    with open("data.txt", "r") as f:
        content = f.read()        # Read all
        # f.readline()            # Read one line
        # f.readlines()           # Read all lines as list
    
    # Reading line by line
    with open("data.txt", "r") as f:
        for line in f:
            print(line.strip())
    
    # Binary files
    with open("data.bin", "wb") as f:
        f.write(b"Binary data")
    
    with open("data.bin", "rb") as f:
        data = f.read()
    
    # Append mode
    with open("data.txt", "a") as f:
        f.write("Appended line\n")
    
    # File position
    with open("data.txt", "r") as f:
        f.seek(0)         # Go to beginning
        pos = f.tell()    # Get current position
    
    # pathlib
    from pathlib import Path
    
    path = Path("data.txt")
    path.write_text("Hello")
    content = path.read_text()
    path.exists()
    path.is_file()
    path.is_dir()
    path.unlink()  # Delete file
    
    # Directory operations
    import os
    
    os.listdir(".")
    os.mkdir("new_dir")
    os.makedirs("path/to/dir", exist_ok=True)
    os.remove("file.txt")
    os.rmdir("dir")
    os.rename("old.txt", "new.txt")
    
    Path("dir").mkdir(exist_ok=True)
    Path("file.txt").unlink(missing_ok=True)
```

### Regular Expressions

```python
import re

def regex_demo():
    # Match
    pattern = r"\d+"
    text = "There are 123 apples"
    
    match = re.search(pattern, text)
    if match:
        print(match.group())
        print(match.start())
        print(match.end())
    
    # Find all
    matches = re.findall(r"\d+", "123 and 456")
    print(matches)  # ['123', '456']
    
    # Split
    parts = re.split(r"\d+", "a1b2c3")
    print(parts)  # ['a', 'b', 'c', '']
    
    # Replace
    result = re.sub(r"\d+", "X", "a1b2c3")
    print(result)  # 'aXbXcX'
    
    # Groups
    pattern = r"(\d{4})-(\d{2})-(\d{2})"
    match = re.search(pattern, "2024-01-15")
    if match:
        year, month, day = match.groups()
        print(year, month, day)
    
    # Named groups
    pattern = r"(?P<year>\d{4})-(?P<month>\d{2})-(?P<day>\d{2})"
    match = re.search(pattern, "2024-01-15")
    if match:
        print(match.group("year"))
    
    # Compile pattern
    pattern = re.compile(r"\d+")
    matches = pattern.findall("123 and 456")
    
    # Flags
    re.search(r"hello", "HELLO", re.IGNORECASE)
    re.search(r"^pattern", text, re.MULTILINE)
    re.search(r".*", text, re.DOTALL)
```

### Date and Time

```python
from datetime import datetime, date, time, timedelta

def datetime_demo():
    # Current date and time
    now = datetime.now()
    today = date.today()
    current_time = datetime.now().time()
    
    # Create datetime
    dt = datetime(2024, 1, 15, 14, 30, 0)
    d = date(2024, 1, 15)
    t = time(14, 30, 0)
    
    # Components
    print(now.year)
    print(now.month)
    print(now.day)
    print(now.hour)
    print(now.minute)
    print(now.second)
    print(now.weekday())
    
    # Formatting
    print(now.strftime("%Y-%m-%d"))
    print(now.strftime("%H:%M:%S"))
    print(now.strftime("%A, %B %d, %Y"))
    
    # Parsing
    dt = datetime.strptime("2024-01-15", "%Y-%m-%d")
    
    # Timedelta
    tomorrow = now + timedelta(days=1)
    week_ago = now - timedelta(weeks=1)
    
    delta = timedelta(days=1, hours=2, minutes=30)
    print(delta.total_seconds())
    
    # Comparison
    if now > dt:
        print("now is later")
    
    # ISO format
    print(now.isoformat())
    
    # Timestamp
    timestamp = now.timestamp()
    from_timestamp = datetime.fromtimestamp(timestamp)
```

## 10. Tooling and Ecosystem

### pip and Virtual Environments

```bash
# Install packages
pip install package-name
pip install package-name==1.0.0
pip install package-name>=1.0.0

# Uninstall
pip uninstall package-name

# List installed packages
pip list
pip freeze > requirements.txt

# Install from requirements
pip install -r requirements.txt

# Search packages
pip search package-name

# Show package info
pip show package-name

# Upgrade package
pip install --upgrade package-name

# Create virtual environment
python -m venv myenv

# Activate
# Windows:
myenv\Scripts\activate
# macOS/Linux:
source myenv/bin/activate

# Deactivate
deactivate
```

### Testing

```python
# unittest
import unittest

class TestCalculator(unittest.TestCase):
    def test_add(self):
        self.assertEqual(2 + 3, 5)
    
    def test_subtract(self):
        self.assertEqual(5 - 3, 2)
    
    def test_divide_by_zero(self):
        with self.assertRaises(ZeroDivisionError):
            1 / 0

if __name__ == '__main__':
    unittest.main()

# pytest (more popular)
def test_add():
    assert 2 + 3 == 5

def test_subtract():
    assert 5 - 3 == 2

def test_divide_by_zero():
    import pytest
    with pytest.raises(ZeroDivisionError):
        1 / 0

# Fixtures
import pytest

@pytest.fixture
def sample_data():
    return [1, 2, 3, 4, 5]

def test_sum(sample_data):
    assert sum(sample_data) == 15

# Parametrize
@pytest.mark.parametrize("input,expected", [
    (2, 4),
    (3, 9),
    (4, 16),
])
def test_square(input, expected):
    assert input ** 2 == expected
```

### Type Checking with mypy

```python
# mypy checks type hints
from typing import List, Optional

def greet(name: str) -> str:
    return f"Hello, {name}!"

def sum_numbers(numbers: List[int]) -> int:
    return sum(numbers)

def find_user(user_id: int) -> Optional[str]:
    if user_id > 0:
        return f"User {user_id}"
    return None

# Run: mypy script.py
```

### Linting and Formatting

```bash
# pylint
pylint script.py

# flake8
flake8 script.py

# black (formatter)
black script.py

# isort (import sorter)
isort script.py
```

## 11. Best Practices

### Code Style (PEP 8)

```python
# Use 4 spaces for indentation
def my_function():
    if condition:
        do_something()

# Maximum line length: 79 characters
# Use lowercase_with_underscores for functions and variables
def calculate_total(items):
    pass

# Use CapitalizedWords for classes
class MyClass:
    pass

# Constants in UPPERCASE
MAX_SIZE = 100
API_KEY = "secret"

# Imports at top, grouped
import os
import sys

import numpy as np
import pandas as pd

from mypackage import mymodule

# Two blank lines between top-level definitions
class ClassOne:
    pass


class ClassTwo:
    pass

# Docstrings
def function(arg):
    """
    Short description.
    
    Longer description if needed.
    
    Args:
        arg: Description of arg
    
    Returns:
        Description of return value
    """
    pass

# List comprehensions
squares = [x**2 for x in range(10)]

# Not too complex
result = [
    process(x)
    for x in data
    if is_valid(x)
]
```

### Common Idioms

```python
# Check for empty
if not my_list:
    print("List is empty")

# Check for None
if value is None:
    print("Value is None")

# Enumerate instead of range(len())
for index, item in enumerate(items):
    print(f"{index}: {item}")

# Zip for parallel iteration
for name, age in zip(names, ages):
    print(f"{name}: {age}")

# Context managers
with open("file.txt") as f:
    data = f.read()

# Dictionary get with default
value = mydict.get("key", "default")

# Set default
mydict.setdefault("key", "default")

# String formatting
name = "Alice"
age = 30
print(f"{name} is {age} years old")

# Unpacking
first, *middle, last = [1, 2, 3, 4, 5]

# Dictionary unpacking
merged = {**dict1, **dict2}

# Function argument unpacking
args = [1, 2, 3]
function(*args)

kwargs = {"a": 1, "b": 2}
function(**kwargs)
```

## 12. Conclusion

### Key Takeaways

Python is a versatile, powerful programming language:

1. **Simplicity**: Clean, readable syntax
2. **Versatility**: Web, data science, AI, automation
3. **Rich Ecosystem**: Extensive standard library and third-party packages
4. **Community**: Large, active, and supportive community
5. **Career Opportunities**: High demand across industries
6. **Learning Curve**: Beginner-friendly yet powerful
7. **Multi-paradigm**: OOP, functional, procedural

### Learning Path

1. **Basics**: Master syntax, data types, control flow
2. **Data Structures**: Lists, dicts, sets, tuples
3. **Functions**: Write reusable code
4. **OOP**: Classes, inheritance, polymorphism
5. **Modules**: Use and create modules
6. **File I/O**: Read and write files
7. **Error Handling**: Handle exceptions gracefully
8. **Standard Library**: Explore built-in modules
9. **Third-party Packages**: NumPy, Pandas, Requests
10. **Frameworks**: Django, Flask, FastAPI

### Resources

- **Official Docs**: docs.python.org
- **Tutorial**: docs.python.org/tutorial
- **PyPI**: pypi.org (Python Package Index)
- **Real Python**: realpython.com
- **Python.org**: python.org

### Next Steps

1. Build projects (web apps, scripts, data analysis)
2. Learn frameworks (Django, Flask, FastAPI)
3. Explore data science (NumPy, Pandas, Matplotlib)
4. Study machine learning (scikit-learn, TensorFlow, PyTorch)
5. Contribute to open source
6. Join Python communities

This guide covers essential Python programming concepts. Continue practicing and building projects to master the language!
