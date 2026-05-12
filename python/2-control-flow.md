# Control Flow

## Conditional Blocks

### Conditional Statements
Conditional statements are used to control the flow of a program based on whether certain conditions evaluate to `True` or `False`.

#### The `if` statement
The simplest form of branching. The code block inside executes only if the specified condition is `True`.
```python
temperature = 25
if temperature > 20:
    print("It's a warm day.") 
# Output: It's a warm day.
```

#### The `if-else` statement
Provides an alternative code block that executes if the `if` condition is `False`.
```python
temperature = 15
if temperature > 20:
    print("It's a warm day.")
else:
    print("It's a cold day.")
# Output: It's a cold day.
```

#### The `if-elif` and `if-elif-else` statement
Allows checking multiple sequential conditions (`elif` is short for "else if"). The first block with a condition that evaluates to `True` will execute, and the rest are skipped. The final `else` is optional and catches any case that didn't match.
```python
score = 85

if score >= 90:
    print("Grade: A")
elif score >= 80:
    print("Grade: B")
elif score >= 70:
    print("Grade: C")
else:
    print("Grade: D or F")
# Output: Grade: B
```

#### The `match` and `case` statements (Python 3.10+)
Also known as Structural Pattern Matching, it behaves similarly to "switch-case" in other languages. It compares a variable against several possible pattern values. The underscore `_` acts as the default "wildcard" catch-all.

```python
status_code = 404

match status_code:
    case 200:
        print("OK")
    case 404:
        print("Not Found")
    case 500:
        print("Server Error")
    case _:  # Wildcard (Default case)
        print("Unknown Status")
# Output: Not Found
```

You can combine multiple potential matching values in a single `case` using the pipe symbol `|` (acting as an OR operator):
```python
command = "EXIT"

match command:
    case "START" | "GO":
        print("System starting...")
    case "EXIT" | "QUIT" | "STOP":
        print("System shutting down...")
# Output: System shutting down...
```

### Multiple Conditional Statements
You can evaluate multiple conditions simultaneously within a single statement using boolean logic operators (`and`, `or`, `not`).
```python
age = 22
has_license = True

if age >= 18 and has_license:
    print("You are allowed to drive.")
else:
    print("You cannot drive.")
```

### Nesting Conditional Statements
You can place conditional statements inside other conditional statements to check for layered or more specific conditions.
```python
num = 10

if num >= 0:
    if num == 0:
        print("The number is Zero")
    else:
        print("The number is Positive")
else:
    print("The number is Negative")
# Output: The number is Positive
```

---

## Loops

### The `pass` instruction
In Python, code blocks (like loops or conditions) cannot be empty. The `pass` instruction acts as a null operation placeholder—it does absolutely nothing but prevents syntactic errors when a statement is required.
```python
if True:
    pass # Placeholder for code to be written later
```

### Building Loops

#### The `while` loop
Executes a block of code repeatedly as long as a specified condition remains `True`. You must ensure the condition eventually becomes `False` to avoid infinite loops.
```python
count = 1
while count <= 3:
    print(f"Iteration {count}")
    count += 1
# Output:
# Iteration 1
# Iteration 2
# Iteration 3
```

#### The `for` loop, `range()`, and `in`
The `for` loop is used to iterate over a sequence or any iterable object.
* **`in`**: Used to point to the sequence being traversed.
* **`range()`**: A built-in function that generates a sequence of numbers.
    * `range(stop)`: Numbers from `0` up to (but not including) `stop`.
    * `range(start, stop)`: Numbers from `start` up to `stop`.
    * `range(start, stop, step)`: Numbers with a custom increment `step`.

```python
# Using range(stop)
for i in range(3):
    print(i, end=" ") # Output: 0 1 2

print()

# Using range(start, stop, step)
for i in range(10, 25, 5):
    print(i, end=" ") # Output: 10 15 20
```

### Iterating Through Sequences
`for` loops can directly traverse elements in strings, lists, tuples, or dicts without needing an index tracker.
```python
# Iterating through a String
word = "Py"
for char in word:
    print(char)
# Output:
# P
# y

# Iterating through a List
fruits = ["Apple", "Banana"]
for fruit in fruits:
    print(fruit)
```

### Expanding Loops with `else`
Python allows an optional `else` clause attached to loops. The `else` block executes **only if the loop completed naturally** (i.e., the condition became `False` in `while`, or the iteration sequence ran out in `for`). If the loop is terminated prematurely using a `break`, the `else` block is skipped.

#### The `while-else` loop
```python
x = 1
while x < 3:
    print(x)
    x += 1
else:
    print("Loop finished normally!")
# Output:
# 1
# 2
# Loop finished normally!
```

#### The `for-else` loop
This is particularly useful for searching items in a collection.
```python
numbers = [1, 3, 5, 7]

for num in numbers:
    if num % 2 == 0:
        print("Found an even number!")
        break
else:
    print("No even numbers found in the list.")
# Output: No even numbers found in the list.
```

### Nesting Loops and Conditional Statements
You can nest loops inside other loops, and combine them freely with conditional `if` logic to handle complex workflows.
```python
# Nested For Loops
for i in range(1, 3):
    for j in range(1, 3):
        print(f"({i}, {j})", end=" ")
# Output: (1, 1) (1, 2) (2, 1) (2, 2)
```

### Controlling Loop Execution
You can interrupt or fine-tune the behavior of loop iterations dynamically.

#### The `break` statement
Terminates the loop completely and immediately jumps to the first statement outside the loop block.
```python
for num in range(1, 10):
    if num == 4:
        break # Exits the entire loop
    print(num, end=" ")
# Output: 1 2 3
```

#### The `continue` statement
Skips the remaining statements in the **current iteration** and immediately jumps back to the beginning of the next cycle of the loop.
```python
for num in range(1, 5):
    if num == 3:
        continue # Skips printing 3
    print(num, end=" ")
# Output: 1 2 4
```
