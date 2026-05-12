# Python Fundamentals

## Logic and Structure

### Keywords
Reserved words that have special meanings to the interpreter and cannot be used as variable names.

| Category              | Keywords                                                          |
| --------------------- | ----------------------------------------------------------------- |
| Logical Values        | `True`, `False`, `None`                                           |
| Boolean Operators     | `and`, `or`, `not`                                                |
| Identity & Membership | `is`, `in`                                                        |
| Control Flow          | `if`, `else`, `elif`, `for`, `while`, `break`, `continue`, `pass` |
| Pattern Matching      | `match`, `case`                                                   |
| Functions & Classes   | `def`, `return`, `lambda`, `class`, `yield`                       |
| Exceptions            | `try`, `except`, `finally`, `raise`, `assert`                     |
| Imports               | `import`, `from`, `as`                                            |
| Scope                 | `global`, `nonlocal`                                              |
| Context Management    | `with`                                                            |
| Memory / References   | `del`                                                             |
| Async                 | `async`, `await`                                                  |

### Indentation
Leading whitespace at the beginning of a line of code used to define block scope.

* **Executable Blocks**: Replaces curly braces `{}` used in other languages to define code blocks.
* **Syntax Rule**: Incorrect or mixed indentation raises `IndentationError` or `TabError`.
* **Style Convention (PEP 8)**: Recommends exactly **4 spaces** per indentation level.

```python
if True:
    print("Indented block") # Output: Indented block
```

### Comments
Source code annotations ignored by the Python interpreter.

* **Single-line**: Begins with a hash `#` symbol. Anything following it on that line is ignored.
* **Multi-line**: Not natively supported; implemented using consecutive `#` tags or multi-line string literals (`"""` / `'''`) not assigned to variables.

```python
# Single line comment
print("Visible") # Output: Visible

"""
Multi-line
docstring comment
"""
print("Code runs") # Output: Code runs
```

---

## Literals and Variables

### Data Types
Built-in data types representing different data structures and values.

| Category        | Type / Structure | Description                           | Example                 |
| --------------- | ---------------- | ------------------------------------- | ----------------------- |
| Text Type       | `str`            | Sequence of characters                | `"hello"`               |
| Numeric Types   | `int`            | Integer numbers                       | `10`, `-5`, `0`         |
| Numeric Types   | `float`          | Decimal numbers                       | `3.14`, `-0.5`          |
| Numeric Types   | `complex`        | Complex numbers                       | `2 + 3j`                |
| Boolean Type    | `bool`           | Boolean values                        | `True`, `False`         |
| Null Type       | `NoneType`       | Absence of value                      | `None`                  |
| Sequence Types  | `list`           | Mutable ordered collection            | `[1, 2, 3]`             |
| Sequence Types  | `tuple`          | Immutable ordered collection          | `(1, 2, 3)`             |
| Sequence Types  | `range`          | Immutable numeric sequence            | `range(5)`              |
| Mapping Types   | `dict`           | Key-value collection                  | `{"fruit": "Apple"}`    |
| Set Types       | `set`            | Unordered collection of unique values | `{1, 2, 3}`             |
| Set Types       | `frozenset`      | Immutable set                         | `frozenset([1, 2])`     |
| Binary Types    | `bytes`          | Immutable binary data                 | `b"hello"`              |
| Binary Types    | `bytearray`      | Mutable binary data                   | `bytearray(b"hello")`   |
| Binary Types    | `memoryview`     | Memory-efficient binary view          | `memoryview(b"abc")`    |

### Scientific notation (EXTRA)
A method representing extremely large or small numbers using the letter `e` or `E` (powers of 10).

```python
num = 51000
print(f"{num:e}")    # Output: 5.100000e+04
print(f"{num:.2e}")  # Output: 5.10e+04

num_small = 1e-5
print(f"{num_small:.6f}") # Output: 0.000010
```

### Accuracy of Floating-Point Numbers (EXTRA)
Binary formats cannot represent certain decimal fractions perfectly, leading to minor rounding variances.

* **Comparison Safety**: Use `round()` or verify absolute differences are below a chosen tolerance threshold.

```python
print(0.1 + 0.2)          # Output: 0.30000000000000004
print(0.1 + 0.2 == 0.3)   # Output: False
print(round(0.1 + 0.2, 1) == 0.3) # Output: True
```

### Numeral systems (EXTRA)
Integers can be represented and converted directly in various mathematical bases.

* **Binary (Base-2)**: Prefixed with `0b` or `0B`.
* **Octal (Base-8)**: Prefixed with `0o` or `0O`.
* **Decimal (Base-10)**: Standard notation (no prefix).
* **Hexadecimal (Base-16)**: Prefixed with `0x` or `0X`.

```python
# Base Representations
print(0b1010) # Output: 10
print(0o12)   # Output: 10
print(0xA)    # Output: 10

# Integer Base Conversions
print(bin(10))  # Output: '0b1010'
print(oct(10))  # Output: '0o12'
print(hex(10))  # Output: '0xa'

# String-to-Base Conversions
print(int("1010", 2)) # Output: 10
print(int("a", 16))   # Output: 10
```

### Variables
Identifiers acting as pointers to objects in memory. Created instantly upon first value assignment (`=`).

* **Case-Sensitivity**: `fruit` and `Fruit` are completely unique identifiers.
* **Descriptive Naming**: Follow standard **`snake_case`** style.
* **Character Constraints**: Must begin with a **letter** or **underscore** (`_`). Can only contain **alphanumeric** characters and underscores. Cannot use reserved Python **keywords**.

#### Assignment Techniques
```python
# Single Assignment
fruit = "Apple"

# Multiple Assignment
x, y, z = 1, 2, 3
print(x, y, z) # Output: 1 2 3

# Chained Assignment
x = y = z = 10
print(x, y, z) # Output: 10 10 10

# Variable Swapping
a, b = 10, 20
a, b = b, a
print(a, b) # Output: 20 10
```

#### Dynamic Typing
Variables can dynamically rebind to objects of different data types during runtime.

```python
val = 10
print(type(val)) # Output: <class 'int'>

val = "changed"
print(type(val)) # Output: <class 'str'>
```

### Type Casting
Converting values from one data type to another.

* **Implicit Conversion**: Python automatically converts the type to prevent loss during operations (e.g., int to float).
* **Explicit Conversion**: Manually forcing a conversion via constructor functions: **`int()`**, **`float()`**, **`str()`**, **`bool()`**.

```python
# Implicit
result = 10 + 2.5
print(type(result)) # Output: <class 'float'>

# Explicit
x = int("10") 
print(x) # Output: 10

z = float(5) 
print(z) # Output: 5.0
```

---

## Operators

### Arithmetic operators
Execute mathematical computations directly on numerical operands.

| Operator | Name           | Description                                | Example               | Return Type  |
| -------- | -------------- | ------------------------------------------ | --------------------- | ------------ |
| `+`      | Addition       | Adds two operands                          | `10 + 3` -> `13`      | Int or Float |
| `-`      | Subtraction    | Subtracts right from left                  | `10 - 3` -> `7`       | Int or Float |
| `*`      | Multiplication | Multiplies two operands                    | `10 * 3` -> `30`      | Int or Float |
| `/`      | Division       | Divides left by right                      | `10 / 3` -> `3.33333` | Float        |
| `//`     | Floor Division | Divides and rounds down to nearest integer | `10 // 3` -> `3`      | Int or Float | 
| `%`      | Modulus        | Returns integer remainder of division      | `10 % 3` -> `1`       | Int or Float | 
| `**`     | Exponentiation | Raises left to the power of right          | `10 ** 3` -> `1000`   | Int or Float | 

### String operators
Dedicated syntax designed to manipulate or merge string sequences.

| Operator | Name          | Description                                                        | Example                     |
| -------- | ------------- | ------------------------------------------------------------------ | --------------------------- |
| `+`      | Concatenation | Combines string items                                              | `"Py" + "thon"` -> `Python` |
| `*`      | Repetition    | Multiplies string sequence count (requires integer)                | `"Py" * 3` -> `PyPyPy`      |

### Assignment and shortcut operators
Store and assign values, often integrating mathematics or bitwise operations into a consolidated step.

| Operator | Name                           | Example          | Equivalent To           |
| -------- | ------------------------------ | ---------------- | ----------------------- |
| `=`      | Assignment                     | `x = 5`          | `x = 5`                 |
| `+=`     | Addition Assignment            | `x += 5`         | `x = x + 5`             |
| `-=`     | Subtraction Assignment         | `x -= 5`         | `x = x - 5`             |
| `*=`     | Multiplication Assignment      | `x *= 5`         | `x = x * 5`             |
| `/=`     | Division Assignment            | `x /= 5`         | `x = x / 5`             |
| `//=`    | Floor Division Assignment      | `x //= 5`        | `x = x // 5`            |
| `%=`     | Modulus Assignment             | `x %= 5`         | `x = x % 5`             |
| `**=`    | Exponentiation Assignment      | `x **= 5`        | `x = x ** 5`            |
| `&=`     | Bitwise AND Assignment         | `x &= 5`         | `x = x & 5`             |
| `\|=`    | Bitwise OR Assignment          | `x \|= 5`        | `x = x \| 5`            |
| `^=`     | Bitwise XOR Assignment         | `x ^= 5`         | `x = x ^ 5`             |
| `>>=`    | Right Shift Assignment         | `x >>= 5`        | `x = x >> 5`            |
| `<<=`    | Left Shift Assignment          | `x <<= 5`        | `x = x << 5`            |
| `:=`     | Walrus (Assignment Expression) | `print(x := 5)`  | `x = 5` <br> `print(x)` |

### Unary operators
Affects a solitary operand logic or sign value directly.

| Operator | Name                           | Example                                      |
| -------- | ------------------------------ | -------------------------------------------- |
| `+`      | Positive Unary (Identity)      | `+5` -> 5                                    |
| `-`      | Negative Unary (Negation)      | `x = 5; -x` -> `-5` <br> `x = -5; -x` -> `5` |
| `~`      | Bitwise NOT (Bits inversion)   | `~5` -> `-6` <br> `~(-10)` -> `9`            |
| `not`    | Logical NOT (Logical Negation) | `not True` -> `False` <br> `not 0` -> `True` |

### Boolean operators
Performs foundational logic checks and evaluates object identities.

| Operator | Name                      | Description                                     | Example                     |
| -------- | ------------------------- | ----------------------------------------------- | --------------------------- | 
| `not`    | Logical NOT (Negation)    | Inverts the boolean state                       | `not True` -> `False`       | 
| `and`    | Logical AND (Conjunction) | Returns `True` only if both operands are true   | `True and False` -> `False` | 
| `or`     | Logical OR (Disjunction)  | Returns `True` if any operand is true           | `True or False` -> `True`   | 
| `is`     | Identity                  | Returns `True` if referencing same object       | `a is a` -> `True`          | 
| `is not` | Identity                  | Returns `True` if referencing different objects | `a is not a` -> `False`     | 

### Boolean expressions
Formulations returning boolean states. Read Left-to-Right.

* **Short-Circuiting**: Processing immediately halts once the logic finalizes (e.g., finding False in `and`, or True in `or`). The last evaluated item value is returned.
* **Falsy Values**: `0`, `""` (empty str), `[]` (empty list), and `None`.
* **Truthy Values**: All populated, non-empty values.

```python
print("Python" or 20) # Output: "Python"
print("Python" and 20) # Output: 20
```

### Relational operators
Binary comparison operators. Continually return explicit boolean outputs.

| Operator | Name                     | Description                                     | Example               |
| -------- | ------------------------ | ----------------------------------------------- | --------------------- | 
| `==`     | Equal                    | Verifies left matches right value               | `10 == 20` -> `False` |
| `!=`     | Not equal                | Verifies left value differs from right          | `10 != 20` -> `True`  |
| `>`      | Greater than             | Checks if left value is larger than right       | `10 > 20` -> `False`  |
| `<`      | Less than                | Checks if left value is smaller than right      | `10 < 20` -> `True`   |
| `>=`     | Greater than or equal to | Checks if left is larger or identical to right  | `10 >= 10` -> `True`  |
| `<=`     | Less than or equal to    | Checks if left is smaller or identical to right | `10 <= 20` -> `True`  |

### Priorities and binding
Determines evaluation priority, cascading from highest ranking to lowest.

| Precedence | Operator(s)         | Category                       | Associativity | Example                | Description                         |
| ---------- | ------------------- | ------------------------------ | ------------- | ---------------------- | ----------------------------------- |
| 1          | `()`                | Parentheses                    | Left-to-right | `(2 + 3) * 4` -> `20`  | Forces overrides of defaults        |
| 2          | `**`                | Exponentiation                 | Right-to-left | `2 ** 3 ** 2` -> `512` | Evaluated as 2 ** (3 ** 2)          |
| 3          | `+x`, `-x`, `~x`    | Unary Plus, Minus, Bitwise NOT | Right-to-left | `-5 + 3` -> `-2`       | Unary operand operation             |
| 4          | `*`, `/`, `//`, `%` | Multiplicative Arithmetic      | Left-to-right | `10 / 2 * 3` -> `15.0` | Evaluates left-to-right sequence    |
| 5          | `+`, `-`            | Additive Arithmetic / String   | Left-to-right | `5 + 3 - 2` -> `6`     | Addition / Concatenation operations |
| 6          | `>>`,  `<<`         | Bitwise Shifts                 | Left-to-right | `2 << 2` -> `8`        | Modifies bits left or right         |
| 7          | `&`                 | Bitwise AND                    | Left-to-right | `5 & 3` -> `1`         | Logical bitwise intersection        |
| 8          | `^`                 | Bitwise XOR                    | Left-to-right | `5 ^ 3` -> `6`         | Exclusive OR bit logic              |
| 9          | `\|`                | Bitwise OR                     | Left-to-right | `5 \| 3` -> `7`        | Inclusive OR bit logic              |

**Logical Operators Precedence**
| Precedence | Operator(s) | Category    | Associativity | Example                             | Description                                       |
| ---------- | ----------- | ----------- | ------------- | ----------------------------------- | ------------------------------------------------- |
| 1          | `not`       | Logical NOT | Right-to-left | `not False or True` -> `True`       | Highest logical operator priority                 |
| 2          | `and`       | Logical AND | Left-to-right | `True or False and False` -> `True` | Intermediate priority; short-circuit evaluation   |
| 3          | `or`        | Logical OR  | Left-to-right | `True or False` -> `True`           | Lowest logical priority; short-circuit evaluation |

---

## Console I/O

### The `print()` function
Outputs text directly to the standard console stream.

* **`sep`**: Defines spacer placed between multiple arguments (Default: space `" "`).
* **`end`**: Defines termination output value (Default: newline `\n`).

```python
print("A", "B", sep="-") # Output: A-B
print("X", end="...")
print("Y")               # Output: X...Y
```

### The `input()` function
Reads a text entry line typed directly by the console user.

* **Data Type Requirement**: The incoming value is **always returned as a string (`str`)**.
* **Mathematical Processing**: Numeric operations require nesting `input()` inside an explicit cast construct like **`int()`** or **`float()`**.

```python
# Reading strings
name = input("Enter name: ") # If input is "Alex"
print(name)                  # Output: Alex

# Reading/Converting Numeric Integers
age = int(input("Enter age: ")) # Input "30" parses to int 30
print(age + 1)                  # Output: 31
```
