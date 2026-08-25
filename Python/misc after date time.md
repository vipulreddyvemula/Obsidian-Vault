## 1. `print()` advanced features — Page 100–101

```py
print(value1, value2, sep=' ', end='\n', file=sys.stdout, flush=False)
```
### Important:

- `sep` → separator between values
- `end` → what comes after printing
- `flush=True` → forces output immediately; useful for progress/logging

Example:
```py
print(1, 2, 3, sep="-")
# 1-2-3

print("Hello", end=" ")
print("World")
# Hello World
```

`flush=True` is mainly useful for **real-time output/logging**.
## Functions — Pages 108–114
### Define

```
def my_function():
    print("Hello")
```

### Call

```
my_function()
```

### Basic idea

```
def → define function
()  → parameters
return → send result back
```

---

## Passing arguments

```
def greet(name):
    print("Hello", name)

greet("Vipul")
```

---

## `*args`

If the number of positional arguments is unknown:

```
def my_function(*kids):
    print(kids)
```

`kids` receives the arguments as a **tuple**.

PDF example uses `*kids`.

---

## Keyword arguments

```
def student(name, age):
    print(name, age)

student(age=20, name="Vipul")
```

Order doesn't matter when using `key=value`.

---

## Passing lists/dictionaries

Python functions can receive lists, dictionaries, strings, numbers, etc. without declaring their type.

```
def show(items):
    for x in items:
        print(x)
```

---

# 4. Return Values — Pages 114–115

### Single value

```
def square(x):
    return x * x
```

### Multiple values

```
def calculate(x):
    return x * 5, x ** 2, x + 10
```

Then:

```
a, b, c = calculate(3)
```

The multiple values are returned together and can be unpacked.

**Remember:** This connects directly to **tuples + unpacking**.

---

# 5. Recursion — Page 116

A function can call itself.

```
def fun(n):
    if n > 0:
        return n + fun(n - 1)
    return 0
```

Must have a **base case**, otherwise recursion doesn't stop.

PDF's flow:

```
fun(6)
 → fun(5)
   → fun(4)
     ...
       → fun(0)
```

You already know recursion from C++/Java, so just remember the Python syntax.

---

# 6. Lambda — Pages 117–119

### Definition

A small **anonymous function**.

```
lambda arguments : expression
```

Example:

```
square = lambda x: x * x
```

Multiple arguments:

```
multiply = lambda a, b: a * b
```

Important limitation:

> Lambda contains **one expression**.

PDF mentions uses with:

- sorting
- `map()`
- `filter()`

For now, just understand the syntax and purpose.

---

# 7. Random Numbers — Pages 120–124

Import:

```
import random
```

### Random integer — inclusive

```
random.randint(1, 10)
```

Can produce **1 through 10**.

### `randrange()`

```
random.randrange(20, 50, 3)
```

Think:

```
start = 20
stop  = 50  → excluded
step  = 3
```

### Random float

```
random.random()
```

→ random float between `0` and `1`.

```
random.uniform(1.0, 10.0)
```

→ random float between specified bounds.

### Random choice

```
random.choice(fruits)
```

→ randomly selects **one element**.

### Seed

```
random.seed(42)
```

Same seed → reproducible sequence/results.

---

# 8. `shuffle()` vs `sample()` — Page 124

### Shuffle

```
numbers = [1, 2, 3, 4, 5]
random.shuffle(numbers)
```

Changes the order of the **original list**.

### Sample

```
random.sample(numbers, 3)
```

Returns a list containing **3 unique randomly selected elements**.

### Remember:

```
shuffle → rearranges original list
sample  → selects elements and returns a list
```

---

# 9. Modules — Pages 125–129

A module is basically a `.py` file containing reusable code.

Example:

### `mymodule.py`

```
def greeting(name):
    print("Hello, " + name)
```

Then another file:

```
import mymodule

mymodule.greeting("Vipul")
```

---

## Module can contain variables too

```
# mymodule.py

person1 = {
    "name": "John",
    "age": 36
}
```

Use:

```
import mymodule

print(mymodule.person1["age"])
```

---

## Module alias

```
import mymodule as mx

print(mx.person1["age"])
```

---

## Import specific thing

```
from mymodule import person1

print(person1["age"])
```