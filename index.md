---
layout: default
title: Python Cheat Sheet
description: A comprehensive Python reference guide covering essential syntax, concepts, and best practices
---

# Python Cheat Sheet

A Python reference guide covering the essential syntax, concepts, and best practices.

## Getting Started
*Essential Python basics: comments, variables, data types, and basic operations*

### Comments
```python
# single-line comment
"""multi-line comment"""
```

### Variables and Data Types
```python
# Numbers
x = 10          # int (integer)
y = 3.14        # float (decimal number)

# Text
name = "Fishy"  # str (string)
message = 'Hello'

# Boolean
flag = True     # bool (True or False)
is_active = False
```

### Check Data Type
```python
type(x)         # <class 'int'>
type(name)      # <class 'str'>
```

### Type Casting (Converting Between Types)
```python
int("5")        # Convert string to integer: 5
float(5)        # Convert integer to float: 5.0
str(5)          # Convert number to string: "5"
bool(1)         # Convert to boolean: True
bool(0)         # Convert to boolean: False
```

### f-strings (Formatted Strings)
```python
print(f"Hello {name}, x={x}")
print(f"Price: ${y:.2f}")  # Format float to 2 decimal places
```

## Naming Conventions ([PEP 8](https://peps.python.org/pep-0008/))
*Python style guide for naming variables, functions, classes, and modules*

| Type                    | Example(s)                          |
|-------------------------|-------------------------------------|
| Functions / Variables   | `snake_case` → `total_count`, `get_user()` |
| Constants               | `UPPER_SNAKE_CASE` → `MAX_SPEED = 120`     |
| Classes                 | `PascalCase` → `class UserProfile:`        |
| Modules / Packages      | `snake_case` → `import my_module`          |
| Private/Internal        | `_single_leading_underscore` → `_helper_function()` |
| [Special (dunder - "double under")](https://peps.python.org/pep-0008/#module-level-dunder-names)        | `__double_leading_and_trailing__` → `__init__`, `__str__` |


## Control Flow
*Conditional statements and loops for program logic and iteration*

### If statements
```python
if x > 5:
    print("Big")
elif x == 5:
    print("Equal")
else:
    print("Small")
```

### Loops
```python
for i in range(5):
    print(i)

while x > 0:
    x -= 1

for i, val in enumerate(["a", "b", "c"]):
    print(i, val)
```

## Data Structures
*Collections for storing and organizing data: lists, tuples, sets, and dictionaries*

### Lists (Ordered, Mutable)
```python
# Creating lists
nums = [1, 2, 3]
fruits = ["apple", "banana", "cherry"]
mixed = [1, "hello", 3.14, True]

# Accessing elements
nums[0]         # First element: 1
nums[-1]        # Last element: 3
nums[1:3]       # Slice: [2, 3]

# Modifying lists
nums.append(4)          # Add to end: [1, 2, 3, 4]
nums.insert(1, 1.5)     # Insert at index: [1, 1.5, 2, 3, 4]
nums.remove(1.5)        # Remove value: [1, 2, 3, 4]
```

### Tuples (Ordered, Immutable)
```python
# Creating tuples
coords = (10, 20)
point = (x, y, z)
single = (42,)  # Note the comma for single element

# Accessing elements (same as lists)
coords[0]       # 10
coords[1]       # 20
```

### Sets (Unordered, Unique Elements)
```python
# Creating sets
colors = {"red", "blue", "green"}
numbers = {1, 2, 3, 3, 4}  # Duplicates removed: {1, 2, 3, 4}

# Set operations
colors.add("yellow")           # Add element
colors.remove("red")           # Remove element
colors.union({"purple"})       # Combine sets
colors.intersection({"red"})   # Common elements
```

### Dictionaries (Key-Value Pairs)
```python
# Creating dictionaries
user = {"name": "Matt", "role": "QA", "age": 30}
scores = {"Alice": 95, "Bob": 87, "Charlie": 92}

# Accessing values
user["name"]            # "Matt"
user.get("email", "N/A")  # Safe access with default

# Modifying dictionaries
user["email"] = "matt@example.com"  # Add/update
user.pop("age")         # Remove and return value

# Iterating
for key, value in user.items():
    print(f"{key}: {value}")
```

## Functions
*Reusable code blocks, lambda functions, and parameter handling*

### Basic Functions
```python
def greet(name="World"):
    """Return a greeting message."""
    return f"Hello {name}"

# Function calls
greet()              # "Hello World"
greet("Alice")       # "Hello Alice"
```

### Docstrings (Function Documentation)
```python
def calculate_area(length, width):
    """
    Calculate the area of a rectangle.
    
    Args:
        length (float): The length of the rectangle
        width (float): The width of the rectangle
    
    Returns:
        float: The area of the rectangle
    
    Example:
        >>> calculate_area(5, 3)
        15.0
    """
    return length * width

# Access docstring
help(calculate_area)  # Shows formatted docstring
print(calculate_area.__doc__)  # Shows raw docstring
```

### Functions with Multiple Parameters
```python
def calculate_volume(length, width, height):
    """Calculate volume of a rectangular box."""
    return length * width * height

def create_user(name, age, role="user"):
    """Create user dictionary with optional role."""
    return {"name": name, "age": age, "role": role}
```

### Unpacking (Destructuring)
```python
# Tuple unpacking
a, b = (1, 2)                    # a=1, b=2
x, y, z = (10, 20, 30)

# List unpacking with rest
first, *rest = [1, 2, 3, 4]      # first=1, rest=[2, 3, 4]
first, second, *others = [1, 2, 3, 4, 5]  # first=1, second=2, others=[3, 4, 5]

# Dictionary unpacking
user_info = {"name": "Alice", "age": 25, "city": "NYC"}
name, age = user_info["name"], user_info["age"]
```

## Comprehensions (Concise Data Structure Creation)
*One-liner syntax for creating lists, sets, and dictionaries from iterables*

### List Comprehensions
```python
# Basic: [expression for item in iterable]
squares = [x**2 for x in range(5)]        # [0, 1, 4, 9, 16]

# With condition: [expression for item in iterable if condition]
even_numbers = [x for x in range(10) if x % 2 == 0]  # [0, 2, 4, 6, 8]

# More complex example
words = ["hello", "world", "python"]
word_lengths = [len(word) for word in words]  # [5, 5, 6]
```

### Set Comprehensions
```python
# Basic: {expression for item in iterable}
unique_chars = {c.lower() for c in "Banana"}  # {'b', 'a', 'n'}

# With condition
vowels = {char for char in "programming" if char in "aeiou"}  # {'o', 'a', 'i'}
```

### Dictionary Comprehensions
```python
# Basic: {key: value for item in iterable}
squares_dict = {x: x**2 for x in range(3)}  # {0: 0, 1: 1, 2: 4}

# From existing data
words = ["apple", "banana", "cherry"]
word_lengths = {word: len(word) for word in words}  # {'apple': 5, 'banana': 6, 'cherry': 6}
```

## String Operations
*Text manipulation, formatting, and common string methods*

```python
text = "Hello World"

# Case conversion
text.upper()        # "HELLO WORLD"
text.lower()        # "hello world"
text.title()        # "Hello World"

# String manipulation
text.replace("World", "Python")  # "Hello Python"
text.strip()        # Remove whitespace
text.split(" ")     # ["Hello", "World"]

# Joining strings
" ".join(["a", "b", "c"])  # "a b c"
",".join(["1", "2", "3"])  # "1,2,3"

# String checking
text.startswith("Hello")   # True
text.endswith("World")     # True
"World" in text            # True
```

## Built-in Functions
*Essential Python functions for working with data and sequences*

```python
# Working with sequences
numbers = [1, 2, 3, 4, 5]
len(numbers)        # 5
sum(numbers)        # 15
min(numbers)        # 1
max(numbers)        # 5
sorted([3, 1, 4])   # [1, 3, 4]

# Boolean functions
any([False, True, False])  # True
all([True, True, True])    # True

# Iteration helpers
list(zip([1, 2], ["a", "b"]))  # [(1, 'a'), (2, 'b')]
list(enumerate(["a", "b"]))    # [(0, 'a'), (1, 'b')]
list(range(5))                 # [0, 1, 2, 3, 4]
```

## File Operations
*Reading from and writing to files with proper file handling*

```python
# Reading files
with open("file.txt", "r") as f:
    content = f.read()      # Read entire file
    lines = f.readlines()   # Read as list of lines

# Writing files
with open("output.txt", "w") as f:
    f.write("Hello, World!")
    f.writelines(["Line 1\n", "Line 2\n"])

# File modes: "r" (read), "w" (write), "a" (append), "r+" (read/write)
```

## Error Handling
*Try-except blocks for managing and recovering from errors gracefully*

```python
try:
    result = 10 / 0
except ZeroDivisionError as e:
    print(f"Division by zero: {e}")
except ValueError as e:
    print(f"Invalid value: {e}")
except Exception as e:
    print(f"Unexpected error: {e}")
else:
    print("No errors occurred")
finally:
    print("This always runs")
```

## Common Modules
*Frequently used Python standard library modules for math, random, system, and data operations*

```python
import math, random, os, sys, json, datetime

# Math operations
math.sqrt(16)       # 4.0
math.pi             # 3.14159...
math.ceil(4.2)      # 5

# Random numbers
random.randint(1, 10)       # Random integer 1-10
random.choice([1, 2, 3])    # Random choice from list

# System operations
os.getcwd()         # Current working directory
sys.argv            # Command line arguments

# JSON handling
data = {"name": "Alice", "age": 30}
json_string = json.dumps(data)  # Convert to JSON string
parsed_data = json.loads(json_string)  # Parse JSON string

# Date and time
now = datetime.datetime.now()
today = datetime.date.today()
```

## Development Tools
*Virtual environments and development setup for Python projects*

### Virtual Environments

#### Standard Python (Built-in)
```bash
# Create virtual environment
python -m venv .venv

# Activate (macOS/Linux)
source .venv/bin/activate

# Activate (Windows)
.venv\Scripts\activate

# Deactivate
deactivate
```

#### uv (Third-party environment tool)
*Note: `uv` is not standard Python but is the preferred environment management tool at Genius Lounge*

```bash
# Install uv as a stand-alone package (recommended)
curl -Ls https://astral.sh/uv/install.sh | bash
# Or, on Windows (with winget):
winget install --id astral-sh.uv -e

# Initialize your folder as a Python project
uv init  

# Additional uv benefits:
uv add package_name        # Add dependency
uv remove package_name     # Remove dependency
uv sync                    # Install dependencies from pyproject.toml
```

### Useful Tips
```python
# Debug printing
print(f"{variable=}")  # Prints: variable=value

# Convert list to comma-separated string
numbers = [1, 2, 3, 4]
",".join(map(str, numbers))  # "1,2,3,4"

# Swap variables
a, b = b, a

# Check if key exists in dictionary
if "key" in my_dict:
    value = my_dict["key"]

# Multiple assignment
x, y, z = 1, 2, 3
```
