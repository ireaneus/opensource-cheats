# 🐍 Python Cheatsheet Summary

## What is Python?
Python is a high-level, interpreted, general-purpose programming language. Known for its readability and simplicity, it's widely used in automation, web development, data science, scripting, and DevOps.

## Key Features
- **Interpreted**: No compilation needed.
- **Dynamic Typing**: No need to declare variable types.
- **Object-Oriented**: Supports classes and objects.
- **Extensive Libraries**: Built-in and third-party modules (e.g., `requests`, `boto3`, `pandas`, etc.).
- **Cross-platform**: Runs on Windows, macOS, Linux.

## Basic Syntax
```python
# Hello World
print("Hello, world!")

# Variables and Types
x = 42           # Integer
name = "Alice"   # String
is_active = True # Boolean

# Conditional
if x > 10:
    print("x is greater than 10")

# Loop
for i in range(3):
    print(i)

# Function
def greet(name):
    return f"Hello, {name}"

## ✅ Basics

### 🔹 What are Python's key features?
- Interpreted
- Dynamically typed
- High-level language
- Garbage collected
- Object-oriented
- Rich standard library
- Large community support

### 🔹 What is PEP 8?
- PEP 8 is the **Python Enhancement Proposal** for style guide and best practices in Python code.

### 🔹 How is memory managed in Python?
- Python uses:
  - Reference counting
  - Garbage collection via `gc` module
  - Private heap memory

---

## 🔄 Variables, Data Types, and Operators

### 🔹 Mutable vs Immutable Types?
- **Mutable**: List, dict, set
- **Immutable**: int, float, str, tuple

### 🔹 Difference between `is` and `==`?
- `is`: identity comparison (same object in memory)
- `==`: value equality

---

## 🔁 Control Structures

### 🔹 What is the difference between `break`, `continue`, and `pass`?
- `break`: exits loop
- `continue`: skips current iteration
- `pass`: does nothing, used as a placeholder

---

## 🧰 Functions and Scope

### 🔹 What are *args and **kwargs?
- `*args`: variable number of positional arguments
- `**kwargs`: variable number of keyword arguments

### 🔹 What is a lambda function?
- Anonymous one-line function:
```python
add = lambda x, y: x + y
```

### 🔹 What is scope in Python?
- LEGB Rule:
  - **L**ocal
  - **E**nclosing
  - **G**lobal
  - **B**uilt-in

---

## 🧱 OOP (Object-Oriented Programming)

### 🔹 Core principles of OOP?
- Encapsulation
- Inheritance
- Polymorphism
- Abstraction

### 🔹 Difference between `@staticmethod` and `@classmethod`?
- `@staticmethod`: No `self` or `cls`, works like a regular function inside a class
- `@classmethod`: Receives `cls`, can access and modify class state

---

## 🛠️ Modules, Packages, and Imports

### 🔹 What is the difference between a module and a package?
- **Module**: Single `.py` file
- **Package**: Directory with an `__init__.py` file

### 🔹 How to install and use third-party packages?
```sh
pip install package_name
```
```python
import package_name
```

---

## 💥 Exceptions and Error Handling

### 🔹 How to handle exceptions in Python?
```python
try:
    # risky code
except ExceptionType as e:
    # handle exception
else:
    # no exceptions
finally:
    # always runs
```

---

## 📚 File Handling

### 🔹 How to read and write a file in Python?
```python
with open('file.txt', 'r') as f:
    content = f.read()

with open('file.txt', 'w') as f:
    f.write("Hello World")
```

---

## 🌐 Common Libraries & Use Cases

| Library    | Use Case             |
|------------|----------------------|
| `requests` | HTTP requests        |
| `re`       | Regular expressions  |
| `json`     | JSON parsing         |
| `datetime` | Date/time handling   |
| `os`       | File system access   |
| `sys`      | System functions     |

---

## 🧪 Testing and Debugging

### 🔹 What are common testing tools in Python?
- `unittest`
- `pytest`
- `doctest`

### 🔹 How to debug Python code?
- Use `print()`
- Use built-in `pdb` module:
```python
import pdb; pdb.set_trace()
```

---

## ⚡ Advanced Concepts

### 🔹 What is a generator?
- Function that yields values lazily using `yield`
```python
def counter():
    yield 1
    yield 2
```

### 🔹 What is a decorator?
- Function that modifies behavior of another function
```python
def decorator(func):
    def wrapper():
        print("Before")
        func()
        print("After")
    return wrapper
```

### 🔹 What is the Global Interpreter Lock (GIL)?
- A mutex that protects access to Python objects, affecting multi-threading in CPython.

---

## 🔗 More Resources
- [Real Python](https://realpython.com/)
- [Python Docs](https://docs.python.org/3/)
- [LeetCode - Python Questions](https://leetcode.com/problemset/all/?language=Python)

---

