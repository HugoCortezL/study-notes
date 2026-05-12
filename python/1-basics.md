# Python Fundamentals

## Python’s logic and structure

### Keywords

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

Indentation refers to the leading whitespace at the beginning of a line of code.
Unlike other programming languages that use curly braces `{}` to define code blocks where indentation improves readability only, Python uses indentation to indicate which statements belong to a specific block.

* Indentation is part of the language's syntax. Incorrect or inconsistent indentation may raise an `IndentationError` or `TabError`.
* The official style guide for Python code (PEP 8) recommends using 4 spaces per indentation level.

### Comments

Comments are notes within the source code that are ignored by the interpreter during execution. They can be used to explain code logic, make the program more readable, disable code during debugging, among other purposes.

#### Types of comments

* Single-line comment: Start with `#`, anything following the hash symbol on the same line is ignored.
    ```python
    # This is a comment
    print("Hello, World!")  # This is a comment
    ```

* Multi-line comment: Python doesn't have a specific syntax for multi-line comments. To write multiple lines, you can:

    * Use a `#` symbol at the beginning of each line
        ```python
        # this is the first line
        # second line
        # final line
        print("Hello, World!")
        ```
    * Use string literals `'''` or `"""`. Python will ignore them if they are not assigned to a variable.
        ```python
        """
        this is the first line
        second line
        final line
        """
        print("Hello, World!")
        ```

## Introduction to literals and variables

### Data Types

| Category        | Type / Structure | Description                           | Example                 |
| --------------- | ---------------- | ------------------------------------- | ----------------------- |
| Text Type       | `str`            | Sequence of characters                | `"hello"`               |
| Numeric Types   | `int`            | Integer numbers                       | `10`, `-5`, `0`         |
| Numeric Types   | `float`          | Decimal numbers                       | `3.14`, `-0.5`          |
| Numeric Types   | `complex`        | Complex numbers                       | `2 + 3j`                |
| Boolean Type    | `bool`           | Boolean values                        | `True`, `False`         |
| Null Type       | `NoneType`       | Represents absence of value           | `None`                  |
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
Scientific notation is used to represent very large or very small numbers using the letter `e` or `E` to indicate the power of 10.

```python
num = 51000
print(f"{num:e}")    # Output: 5.100000e+04
print(f"{num:.2e}")  # Output: 5.10e+04 (rounded to 2 decimal places)
```

```python
num = 1e-5
print(f"{num:.6f}") # Output: 0.000010
```

### Binary, octal, decimal, and hexadecimal numeral systems (EXTRA)

#### Representing Numbers
You can define integers directly in different bases by using specific prefixes.
* Binary (Base-2): Prefix with `0b` or `0B` (e.g., `0b1010`).
* Octal (Base-8): Prefix with `0o` or `0O` (e.g., `0o12`).
* Decimal (Base-10): No prefix (e.g., `10`).
* Hexadecimal (Base-16): Prefix with `0x` or `0X` (e.g., `0xA`)

#### Converting Decimal to Other Bases
Python includes built-in functions to convert a decimal integer into a string representation of another base.
* `bin(number)`: Returns the binary string prefixed with `0b`.
* `oct(number)`: Returns the octal string prefixed with `0o`.
* `hex(number)`: Returns the hexadecimal string prefixed with `0x`.

```python
num = 10
print(bin(num))  # Output: '0b1010'
print(oct(num))  # Output: '0o12'
print(hex(num))  # Output: '0xa'
```

#### Converting Other Bases to Decimal
The `int()` function can convert a string of any base back to a decimal integer by specifying the base as the second argument:
* Binary to Decimal: `int("1010", 2)` returns `10`.
* Octal to Decimal: `int("12", 8)` returns `10`.
* Hexadecimal to Decimal: `int("a", 16)` returns `10`.

### Variables
Variables are names that refer to objects stored in memory.

#### Creating Variables
Unlike some programming languages, you don't need to declare a variable before using it. The variable is created at the moment you first assign a value to it using the `=` operator.

```python
fruit = "Apple"
```

* Variable names are case-sensitive. `fruit` and `Fruit` are treated as two completely different variables.

#### Multiple Assignment
* You can assign values to multiple variables at once
```python
x, y, z = 1, 2, 3
```
* You can assign the same value to multiple variables in one line
```python
x = y = z = 10
```
* Python supports swapping values without a temporary variable
```python
x = 10
y = 20

x, y = y, x
```

#### Dynamic Typing
Python is dynamically typed, meaning you don't need to specify the data type when creating a variable. The same variable can reference objects of different types during execution; the variable name stays the same, but the referenced object changes.
```python
value = 10
value = "hello"
value = [1, 2, 3]
```

* `type()`: Returns the data type of a variable.
```python
a = "ola"
print(type(a)) # Output: <class 'str'>
b = 2
print(type(b)) # Output: <class 'int'>
```

#### Naming Conventions
* Follow `snake_case`
* Use descriptive names
* Must start with a letter or an underscore `_`.
* Cannot start with a number
* Can only contain alphanumeric characters and underscores (`A-Z`, `a-z`, `0-9`, and `_`).
* Cannot be a Python keyword like `if`, `else`, or `while`.

## Operators
### Arithmetic operators
Used to perform mathematical calculations on numbers.

| Operator | Name           | Description                                         | Example               | Return Type  |
| -------- | -------------- | --------------------------------------------------- | --------------------- | ------------ |
| `+`      | Addition       | Adds two operands                                   | `10 + 3` -> `13`      | Int or Float |
| `-`      | Subtraction    | Subtracts the right operand from the left           | `10 - 3` -> `7`       | Int or Float |
| `*`      | Multiplication | Multiplies two operands                             | `10 * 3` -> `30`      | Int or Float |
| `/`      | Division       | Divides the left operand by the right               | `10 / 3` -> `3.33333` | Float        |
| `//`     | Floor Division | Divides and rounds down to the nearest whole number | `10 // 3` -> `3`      | Int or Float | 
| `%`      | Modulus        | Returns the remainder of the division               | `10 % 3` -> `1`       | Int or Float | 
| `**`     | Exponentiation | Raises the left operand to the power of the right   | `10 ** 3` -> `1000`   | Int or Float | 

### String operators
Python utilizes a few operators specifically for manipulating and combining strings.

| Operator | Name          | Description                                                        | Example                    |
| -------- | ------------- | ------------------------------------------------------------------ | -------------------------- |
| `+`      | Concatenation | Joins two strings together                                         | `"Py" + "thon"` -> `Python` |
| `*`      | Repetition    | Repeats a string a specified number of times (requires an integer) | `"Py" * 3` -> `PyPyPy`     |

### Assignment and shortcut operators
Python uses assignment operators to store a value in a variable. It also offers shortcut operators that combine arithmetic or bitwise operations with an assignment.

| Operator | Name                           | Example   | Equivalent To |
| -------- | ------------------------------ | --------- | ------------- |
| `=`      | Assignment                     | `x = 5`   | `x = 5`       |
| `+=`     | Addition Assignment            | `x += 5`  | `x = x + 5`   |
| `-=`     | Subtraction Assignment         | `x -= 5`  | `x = x - 5`   |
| `*=`     | Multiplication Assignment      | `x *= 5`  | `x = x * 5`   |
| `/=`     | Division Assignment            | `x /= 5`  | `x = x / 5`   |
| `//=`    | Floor Division Assignment      | `x //= 5` | `x = x // 5`  |
| `%=`     | Modulus Assignment             | `x %= 5`  | `x = x % 5`   |
| `**=`    | Exponentiation Assignment      | `x **= 5` | `x = x ** 5`  |
| `&=`     | Bitwise AND Assignment         | `x &= 5`  | `x = x & 5`   |
| `|=`     | Bitwise OR Assignment          | `x |= 5`  | `x = x | 5`   |
| `^=`     | Bitwise XOR Assignment         | `x ^= 5`  | `x = x ^ 5`   |
| `>>=`    | Right Shift Assignment         | `x >>= 5` | `x = x >> 5`  |
| `<<=`    | Left Shift Assignment          | `x <<= 5` | `x = x << 5`  |
| `:=`     | Walrus (Assignment Expression) | `print(x := 5)`  | `x = 5` <br> `print(x)` |

### Unary operators
| Operator | Name                         | Example                                      |
| -------- | ---------------------------- | -------------------------------------------- |
| `+`      | Positive Unary (Identity)    | `+5` -> 5                                    |
| `-`      | Negative Unary (Negation)    | `x = 5; -x` -> `-5` <br> `x = -5; -x` -> `5` |
| `~`      | Bitwise NOT (Bits inversion) | `~5` -> `-6` <br> `~(-10)` -> `9`             |
| `not`    | Logical NOT (Logical Negation) | `not True` -> `False` <br> `not 0` -> `True` |

### Boolean operators
| Operator | Name                      | Description                                  | Example |
| -------- | ------------------------- | -------------------------------------------- | ---------- | 
| `not`    | Logical NOT (Negation)    | Inverts the boolean value.                   | `not True` -> `False`| 
| `and`    | Logical AND (Conjunction) | Returns `True` only if both sides are true.  | `True and False` -> `False`| 
| `or`     | Logical OR (Disjunction)  | Returns `True` if at least one side is true. | `True or False` -> `True`| 
| `is`     | Identity                  | Returns `True` if both variables are the same object. | `a is a` -> `True`| 
| `is not` | Identity                  | Returns `True` if both variables are not the same object. | `a is not a` -> `False`| 

### Boolean expressions
A boolean expression is any piece of code that Python can evaluate as either true or false. Python evaluates these expressions from left to right and uses the short-circuit evaluation strategy.

* Short-circuit `and`: If the first value is false, Python returns false without evaluating the second value.
* Short-circuit `or`: If the first value is true, Python returns true without evaluating the second value.

#### The behavior with non-boolean objects
In Python, values such as `0`, `""` (empty string), `[]` (empty list), and `None` are considered falsy. Any other non-empty value is truthy.


Due to short-circuiting, the operators `and` and `or` return the last evaluated value, and not necessarily the pure boolean (`True`/`False`):
```python
result_or = "Python" or 20  
print(result_or) # Output: "Python"
result_and = "Python" and 20  
print(result_and)# Output: 20
```

### Relational operators
Relational operators are used to compare two values ​​or expressions. The result of the comparison will always be a boolean value (`True` or `False`).

| Operator | Name                     | Description                                                                 | Example               |
| -------- | ------------------------ | --------------------------------------------------------------------------- | --------------------- | 
| `==`     | Equal                    | Checks if the left value is equal to the right value.                       | `10 == 20` -> `False` |
| `!=`     | Not equal                | Checks if the left value is different from the right value.                 | `10 != 20` -> `True`  |
| `>`      | Greater than             | Checks if the left value is greater than the right value.                   | `10 > 20` -> `False`  |
| `<`      | Less than                | Checks if the left value is less than the right value.                      | `10 < 20` -> `True`   |
| `>=`     | Greater than or equal to | Checks if the left value is greater than or equal to the right value.       | `10 >= 10` -> `True`  |
| `<=`     | Less than or equal to    | Checks if the left value is less than or equal to the right value.          | `10 <= 20` -> `True`  |

### Priorities and binding
| Precedence | Operator(s)         | Category                       | Associativity | Example                | Description                                                 |
| ---------- | ------------------- | ------------------------------ | ------------- | ---------------------- | ----------------------------------------------------------- |
| 1          | `()`                | Parentheses                    | Left-to-right | `(2 + 3) * 4` -> `20`  | Forces overriding of default precedence.                    |
| 2          | `**`                | Exponentiation                 | Right-to-left | `2 ** 3 ** 2` -> `512` | Evaluated as 2 ** (3 ** 2).                                 |
| 3          | `+x`, `-x`, `~x`    | Unary Plus, Minus, Bitwise NOT | Right-to-left | `-5 + 3` -> `-2`       | Applies directly to a single right-hand operand.            |
| 4          | `*`, `/`, `//`, `%` | Multiplicative Arithmetic      | Left-to-right | `10 / 2 * 3` -> `15.0` | Grouped together; evaluated in order of appearance.         |
| 5          | `+`, `-`            | Additive Arithmetic / String   | Left-to-right | `5 + 3 - 2` -> `6`     | Standard math addition/subtraction or string concatenation. |
| 6          | `>>`,  `<<`         | Bitwise Shifts                 | Left-to-right | `2 << 2` -> `8`        | Shifts binary bits left or right.                           |
| 7          | `&`                 | Bitwise AND                    | Left-to-right | `5 & 3` -> `1`         | Bitwise conjunction or set intersection.                    |
| 8          | `^`                 | Bitwise XOR                    | Left-to-right | `5 ^ 3` -> `6`         | Bitwise exclusive OR.                                       |
| 9          | `|`                 | Bitwise OR                     | Left-to-right | `5 | 3` -> `7`         | Bitwise disjunction or set union.                           |

**Logical Operators**
| Precedence | Operator(s) | Category    | Associativity | Example                             | Description                                        |
| ---------- | ----------- | ----------- | ------------- | ----------------------------------- | -------------------------------------------------- |
| 1          | `not`       | Logical NOT | Right-to-left | `not False or True` -> `True`       | Highest priority among logical operators.          |
| 2          | `and`       | Logical AND | Left-to-right | `True or False and False` -> `True` | Short-circuit evaluation; evaluates before or.     |
| 3          | `or`        | Logical OR  | Left-to-right | `True or False` -> `True`           | Short-circuit evaluation; lowest logical priority. |
