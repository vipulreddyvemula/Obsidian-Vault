# Python Quick Notes — Module 1

## 1. Loops

### `while`

```python
while condition:
    # statements
```

Example:

```python
i = 1
while i <= 5:
    print(i)
    i += 1
```

### `for`

```python
for variable in iterable:
    # statements
```

Example:

```python
for i in range(5):
    print(i)
```

### `range()`

```python
range(stop)                # 0 ... stop-1
range(start, stop)         # start ... stop-1
range(start, stop, step)
```

Examples:

```python
range(5)          # 0, 1, 2, 3, 4
range(2, 6)       # 2, 3, 4, 5
range(2, 10, 2)   # 2, 4, 6, 8
```

> **Remember:** `stop` is excluded.

### Nested Loop

```python
for i in range(1, 4):
    for j in range(1, 3):
        print(i, j)
```

### Loop Control Statements

```python
break       # terminate loop completely
continue    # skip current iteration
pass        # do nothing; placeholder
```

Example:

```python
for i in range(10):
    if i == 3:
        continue
    if i == 7:
        break
    print(i)
```

### Loop `else`

Python allows `else` with loops.

```python
while condition:
    # loop
else:
    # executes when loop finishes normally
```

Example:

```python
i = 0

while i < 3:
    print(i)
    i += 1
else:
    print("Finished")
```

> **Important:** If the loop terminates using `break`, the `else` block does **not** execute.

---

## 2. F-Strings

F-strings allow variables and expressions to be inserted directly inside strings.

### Syntax

```python
f"text {expression}"
```

Example:

```python
name = "John"
age = 30

print(f"My name is {name} and I am {age} years old.")
```

### Expressions Inside `{}`

```python
x = 5
y = 3

print(f"{x} * {y} = {x * y}")
```

Output:

```text
5 * 3 = 15
```

### Decimal Formatting

```python
pi = 3.14159

print(f"{pi:.2f}")
```

Output:

```text
3.14
```

> `:.2f` → floating-point number with **2 decimal places**.

---

## 3. Date & Time — `datetime`

### Import

```python
import datetime
```

### Current Date & Time

```python
x = datetime.datetime.now()
print(x)
```

### Create a Specific Date

```python
x = datetime.datetime(year, month, day)
```

Example:

```python
x = datetime.datetime(2025, 8, 13)
```

### Create Date + Time

```python
x = datetime.datetime(2025, 8, 13, 10, 30, 0)
```

Order:

```text
year, month, day, hour, minute, second
```

### `timedelta`

Used to add or subtract time.

```python
x = datetime.datetime.now()

x = x + datetime.timedelta(hours=5)
```

### `strftime()`

Used to format a `datetime` into a readable string.

```python
x.strftime("format")
```

Important format codes:

| Code | Meaning |
|------|---------|
| `%A` | Full weekday |
| `%B` | Full month name |
| `%d` | Day |
| `%m` | Month number |
| `%Y` | 4-digit year |
| `%H` | Hour |
| `%M` | Minute |
| `%S` | Second |

Example:

```python
x = datetime.datetime(2023, 11, 15)

print(x.strftime("%A, %B %d, %Y"))
```

### Timestamp Example

```python
x.strftime("backup_%Y%m%d_%H%M%S")
```

Result format:

```text
backup_20250812_143045
```

---

## 4. Functions

A function is a block of code that runs when called. It can receive parameters and return data.

### Basic Syntax

```python
def function_name(parameters):
    # code
    return value
```

Example:

```python
def add(a, b):
    return a + b

x = add(2, 3)
```

### Parameter vs Argument

```python
def greet(name):       # name = parameter
    print(name)

greet("Vipul")         # "Vipul" = argument
```

- **Parameter** → variable written in function definition
- **Argument** → actual value passed while calling the function

### Keyword Arguments

```python
def person(name, age):
    print(name, age)

person(age=20, name="John")
```

> With keyword arguments, **argument order doesn't matter**.

### Passing a List to a Function

```python
def show(items):
    for x in items:
        print(x)

fruits = ["apple", "banana", "cherry"]
show(fruits)
```

### Lambda Function

A small anonymous function.

Syntax:

```python
lambda arguments: expression
```

Example:

```python
x = lambda a, b: a * b

print(x(5, 6))
# 30
```

Lambda functions can take multiple arguments.

---

## 5. Random Module

### Import

```python
import random
```

### `randint()`

```python
random.randint(a, b)
```

Generates a random integer from **a to b inclusive**.

Example:

```python
random.randint(1, 10)
```

Possible values:

```text
1, 2, 3, ..., 10
```

> **Both endpoints are included.**

### `randrange()`

```python
random.randrange(start, stop, step)
```

Example:

```python
random.randrange(20, 50, 3)
```

`50` is **not included**.

Think of it like:

```python
range(20, 50, 3)
```

Python randomly selects one of the possible values.

---

## Quick Revision

```text
range(start, stop, step)       → stop excluded

break                          → exit loop
continue                       → skip current iteration
pass                           → do nothing / placeholder

f"{x}"                         → insert value
f"{x:.2f}"                     → 2 decimal places

datetime.datetime.now()        → current date & time
datetime.datetime(Y, M, D)     → create datetime
datetime.timedelta(hours=5)    → add/subtract time
strftime()                     → format datetime

def f(x):                      → normal function
lambda x: expression           → anonymous function

randint(a, b)                  → a AND b included
randrange(a, b, step)          → b excluded
```