

# 🐍 Python List — Tiny Cheat Sheet

## 1. `sort()` vs `sorted()` ⭐⭐⭐

| Function | Syntax | Meaning | Example | Result |
|---|---|---|---|---|
| `sort()` | `L.sort()` | Sorts **original list** | `L=[4,5,2,1]; L.sort()` | `L → [1,2,4,5]` |
| `sorted()` | `sorted(L)` | Returns **new sorted list**; original unchanged | `L=[4,5,2,1]; M=sorted(L)` | `L → [4,5,2,1]`, `M → [1,2,4,5]` |

```python
L = [4,5,2,1]

L.sort()
# L → [1,2,4,5]
```

```python
L = [4,5,2,1]

M = sorted(L)
# L → [4,5,2,1]
# M → [1,2,4,5]
```

**Remember ⭐**

```text
sort()    → changes ORIGINAL list
sorted()  → creates NEW sorted list

L.sort()  → returns None
sorted(L) → returns sorted list
```

```python
L = [4,5,2,1]

L = L.sort()       # ❌ incorrect
L = sorted(L)      # ✅ correct
```

---

# 2. Copying a List ⭐

| Method | Syntax | Meaning | Example | Result |
|---|---|---|---|---|
| `copy()` | `L2=L.copy()` | Separate copy | `L=["a","b"]; M=L.copy()` | `M → ["a","b"]` |
| `list()` | `L2=list(L)` | Alternate copy | `L=["a","b"]; M=list(L)` | `M → ["a","b"]` |
| Slice | `L2=L[:]` | Separate copy | `M=L[:]` | `M → same elements` |

```python
L = ["apple","banana","cherry"]

M = L.copy()
# ['apple','banana','cherry']
```

```text
L2 = L        → ❌ reference, NOT a separate copy
L2 = L.copy() → ✅ separate list
L2 = list(L)  → ✅ separate list
L2 = L[:]     → ✅ separate list
```

---

# 3. Joining Lists ⭐

### `+` Operator

```python
L1 = ["a","b","c"]
L2 = [1,2,3]

L3 = L1 + L2
# ['a','b','c',1,2,3]
```

### Using `append()`

```python
L1 = ["a","b","c"]
L2 = [1,2,3]

for x in L2:
    L1.append(x)

# ['a','b','c',1,2,3]
```

```text
L1 + L2
→ creates combined list

for x in L2:
    L1.append(x)
→ adds elements ONE BY ONE
```

---

# 4. `max()` and `min()` ⭐

| Function | Syntax | Meaning | Example | Output |
|---|---|---|---|---|
| `max()` | `max(L)` | Maximum value | `max([456,700,200])` | `700` |
| `min()` | `min(L)` | Minimum value | `min([456,700,200])` | `200` |

```python
L1 = ['xyz','zara','abc']
L2 = [456,700,200]

max(L1)
# 'zara'

max(L2)
# 700

min(L1)
# 'abc'

min(L2)
# 200
```

---

# 5. `count()` and `index()`

| Function | Syntax | Meaning | Example | Output |
|---|---|---|---|---|
| `count()` | `L.count(x)` | Number of occurrences | `[1,4,2,9,7,8,9,3,1].count(9)` | `2` |
| `index()` | `L.index(x)` | Position of first occurrence | `["apple","banana","cherry"].index("cherry")` | `2` |

```python
fruits = ["apple","banana","cherry"]

fruits.count("cherry")
# 1

fruits.index("cherry")
# 2
```

---

# 6. List Comprehension ⭐⭐⭐

**Purpose:** Create a new list in a shorter way.

### Syntax

```python
newlist = [expression for item in iterable if condition]
```

| Part | Meaning |
|---|---|
| `expression` | What to put in new list |
| `item` | Current item |
| `iterable` | List, tuple, set, `range()`, etc. |
| `condition` | Optional filter |

### Filter Example

```python
fruits = ["apple","banana","cherry","kiwi","mango"]

newlist = [x for x in fruits if "a" in x]

# ['apple','banana','mango']
```

```text
if condition
→ accepts only items where condition = True
```

### Without `if`

```python
newlist = [x for x in fruits]

# ['apple','banana','cherry','kiwi','mango']
```

```text
condition is OPTIONAL
```

### Using `range()`

```python
newlist = [x for x in range(10)]

# [0,1,2,3,4,5,6,7,8,9]
```

### `range()` + Condition

```python
newlist = [x for x in range(10) if x < 5]

# [0,1,2,3,4]
```

### Changing Expression

```python
fruits = ["apple","banana","cherry","kiwi","mango"]

newlist = ["hello" for x in fruits]

# ['hello','hello','hello','hello','hello']
```

### Conditional Expression ⭐

```python
newlist = [x if x != "banana" else "orange" for x in fruits]

# ['apple','orange','cherry','kiwi','mango']
```

```text
if after iterable
→ FILTER

if ... else ... before for
→ CHANGE/MANIPULATE OUTPUT
```

---

# 🔥 MASTER CHEAT — List Comprehension

```text
SYNTAX
[expression for item in iterable if condition]

expression → what goes into new list
item       → current item
iterable   → list / tuple / set / range()
condition  → optional filter


FILTER
[x for x in L if condition]

[x for x in fruits if "a" in x]
→ items containing "a"


NO FILTER
[x for x in L]

→ copies/iterates all items


CHANGE OUTPUT
[x if condition else y for x in L]

→ manipulate each result


EXAMPLES
[x for x in range(10)]
→ [0,1,2,3,4,5,6,7,8,9]

[x for x in range(10) if x < 5]
→ [0,1,2,3,4]

["hello" for x in fruits]
→ hello for every item
```

---

# 7. File Handling ⭐⭐⭐

## `open()`

| Syntax | Meaning |
|---|---|
| `open(filename)` | Open file |
| `open(filename, mode)` | Open with specified mode |

```python
f = open("demofile.txt")
```

Same as:

```python
f = open("demofile.txt", "rt")
```

### File Modes

| Mode | Meaning | If file doesn't exist |
|---|---|---|
| `"r"` | Read | ❌ Error |
| `"a"` | Append | ✅ Creates |
| `"w"` | Write / overwrite | ✅ Creates |
| `"x"` | Create new | ❌ Error if exists |

### Text / Binary

| Mode | Meaning |
|---|---|
| `"t"` | Text — default |
| `"b"` | Binary — e.g. images |

```text
"r" + "t" → "rt"
```

---

# 8. Reading a File ⭐

### Read Entire File

```python
f = open("demofile.txt", "r")
print(f.read())
```

### Read Specific Number of Characters

```python
f = open("demofile.txt", "r")

print(f.read(5))
# Hello
```

```text
read()
→ entire file

read(n)
→ first n characters
```

### `readline()`

```python
f = open("demofile.txt", "r")

print(f.readline())
```

→ reads **one line**

### Read Two Lines

```python
print(f.readline())
print(f.readline())
```

### Loop Through File

```python
f = open("demofile.txt", "r")

for x in f:
    print(x)
```

```text
read()       → entire content
read(n)      → n characters
readline()   → one line
for x in f   → line by line
```

---

# 9. Closing a File ⭐

```python
f = open("demofile.txt", "r")

print(f.readline())

f.close()
```

**Remember:**

```text
f.close()
→ releases the file/resource
```

Not closing may cause:

```text
memory/resource leaks
file locking issues
resource exhaustion
```

---

# 10. Writing to a File ⭐⭐⭐

## Append `"a"`

```python
f = open("demofile2.txt", "a")

f.write("Now the file has more content!")

f.close()
```

| `"a"` | Meaning |
|---|---|
| Append | Add content to end |
| Existing content | Preserved |
| File doesn't exist | Created |

```text
"a"
→ ADD to existing content
→ does NOT erase old content
→ creates file if needed
```

**Useful for:**

```text
logging
adding entries
preserving history
```

---

## Write `"w"`

```python
f = open("demofile3.txt", "w")

f.write("oops! I have deleted the content!")

f.close()
```

| `"w"` | Meaning |
|---|---|
| Write | Overwrites file |
| Existing content | ❌ Erased |
| File doesn't exist | ✅ Created |

```text
"w"
→ OVERWRITE existing content
→ creates file if needed
```

---

# 11. Creating a File

| Mode | Behavior |
|---|---|
| `"x"` | Create new; error if exists |
| `"a"` | Create if doesn't exist |
| `"w"` | Create if doesn't exist |

```python
f = open("myfile.txt", "x")
```

→ creates a new empty file.

```python
f = open("myfile.txt", "w")
```

→ creates file if it doesn't exist.

---

# 12. Delete a File ⭐

```python
import os

os.remove("demofile.txt")
```

### Check Before Delete

```python
import os

if os.path.exists("demofile.txt"):
    os.remove("demofile.txt")
else:
    print("The file does not exist")
```

---

# 13. Delete a Folder

```python
import os

os.rmdir("myfolder")
```

```text
os.remove()
→ delete FILE

os.rmdir()
→ delete FOLDER
```

---

# 14. Useful `os` Functions

| Function | Meaning | Example |
|---|---|---|
| `os.remove()` | Delete file | `os.remove("a.txt")` |
| `os.rmdir()` | Delete folder | `os.rmdir("folder")` |
| `os.rename()` | Rename file | `os.rename("old.txt","new.txt")` |
| `os.listdir()` | List files in current directory | `os.listdir()` |
| `os.getcwd()` | Current working directory | `os.getcwd()` |
| `os.path.exists()` | Check whether path exists | `os.path.exists("a.txt")` |

```python
import os
```

---

# 15. CSV File Handling ⭐⭐⭐

### CSV

```text
CSV = Comma-Separated Values

Rows    → records
Columns → fields
```

```text
Typical delimiter → ,
Other delimiters   → ; or tab
```

---

# 16. CSV Module

```python
import csv
```

| Function | Meaning |
|---|---|
| `csv.reader()` | Read/parse CSV rows |
| `csv.writer()` | Write structured data to CSV |
| `writerow()` | Write one row |

---

# 17. Reading CSV ⭐⭐⭐

### Basic

```python
import csv

csvfile = open("data.csv", "r", newline="")
csvreader = csv.reader(csvfile)

for row in csvreader:
    print(row)

csvfile.close()
```

```text
csv.reader(csvfile)
→ creates reader object
→ reads CSV row by row
→ each row becomes a list of strings
```

### `newline=""`

```python
open("data.csv", "r", newline="")
```

→ handles newline characters consistently across operating systems.

---

# 18. `with open()` — Better Way ⭐⭐⭐

```python
import csv

with open("data.csv", "r", newline="") as csvfile:
    csvreader = csv.reader(csvfile)

    for row in csvreader:
        print(row)
```

```text
with
→ automatically closes file
→ even if an error occurs
```

### Why `csv.reader()`?

```text
File object
→ raw/plain text

csv.reader()
→ understands CSV structure
→ handles delimiters
→ handles quoted fields
→ handles line endings
→ returns rows as lists
```

---

# 19. Access Specific CSV Columns

```python
import csv

with open("data.csv", "r", newline="") as csvfile:
    csvreader = csv.reader(csvfile)

    for row in csvreader:
        name = row[0]
        age = row[1]

        print(name, age)
```

Example CSV:

```text
Alice,30
Bob,25
Charlie,40
```

Output:

```text
Alice 30
Bob 25
Charlie 40
```

```text
row[0] → first column
row[1] → second column
```

---

# 20. Skip CSV Header ⭐⭐⭐

```python
import csv

with open("data.csv", "r") as csvfile:
    reader = csv.reader(csvfile)

    header = next(reader)

    for row in reader:
        print(row)
```

Example:

```text
Name,Age
Alice,30
Bob,25
Charlie,40
```

Output:

```text
['Alice', '30']
['Bob', '25']
['Charlie', '40']
```

```text
next(reader)
→ reads/skips first row (header)
```

---

# 21. Writing to CSV ⭐⭐⭐

### Append One Row

```python
import csv

with open("data.csv", "a", newline="") as csvfile:
    csvwriter = csv.writer(csvfile)

    csvwriter.writerow(["Bob", 25, "Los Angeles"])
```

```text
"a"
→ append CSV data
```

---

# 22. Writing a List to CSV

```python
import csv

with open("new_file.csv", "w", newline="") as csvfile:
    csvwriter = csv.writer(csvfile)

    for row in data:
        csvwriter.writerow(row)
```

```text
data
→ list of lists containing data

csv.writer()
→ converts structured data into proper CSV format
```

### `csv.writer()` handles

```text
delimiters
quotes (if needed)
line endings
```

---

# 23. Create New CSV File

```python
import csv

with open("new_file.csv", "w", newline="") as csvfile:
    csvwriter = csv.writer(csvfile)

    csvwriter.writerow(["Name", "Age", "City"])
    csvwriter.writerow(["Alice", 30, "New York"])
```

Output:

```text
Name,Age,City
Alice,30,New York
```

---

# 🔥🔥 MASTER CHEAT — WEEK 3

```text
SORTING
L.sort()
→ modifies ORIGINAL
→ returns None

sorted(L)
→ creates NEW sorted list
→ original unchanged

L.sort(reverse=True)
→ descending

L.sort(key=str.lower)
→ case-insensitive


COPY
L2 = L.copy()
L2 = list(L)
L2 = L[:]
→ separate copy

L2 = L
→ reference only


JOIN
L1 + L2
→ concatenate

for x in L2:
    L1.append(x)
→ add one by one


INFO
len(L)       → number of elements
L.count(x)   → occurrences
L.index(x)   → first index
max(L)       → maximum
min(L)       → minimum


LIST COMPREHENSION
[expression for item in iterable if condition]

[x for x in L]
→ all items

[x for x in L if condition]
→ filter

[x if condition else y for x in L]
→ manipulate output

[x for x in range(10)]
→ 0 to 9


FILE OPEN
open(file)
open(file, mode)

"r" → read
"a" → append
"w" → overwrite
"x" → create
"t" → text
"b" → binary


READ
f.read()
→ entire file

f.read(n)
→ n characters

f.readline()
→ one line

for x in f:
→ line by line

f.close()
→ close file


WRITE
f.write(x)
→ write content

"a"
→ append, preserve old content
→ create if missing

"w"
→ overwrite
→ create if missing

"x"
→ create new
→ error if exists


WITH
with open(...) as f:
    ...
→ automatically closes file


OS
import os

os.remove(file)
→ delete file

os.rmdir(folder)
→ delete folder

os.rename(old,new)
→ rename

os.listdir()
→ list directory files

os.getcwd()
→ current directory

os.path.exists(path)
→ check existence


CSV
import csv

csv.reader(file)
→ read CSV rows

csv.writer(file)
→ write CSV

writerow(row)
→ write one row

next(reader)
→ skip/read header

row[0]
→ first column

row[1]
→ second column


CSV READ
with open("data.csv","r",newline="") as f:
    reader = csv.reader(f)
    for row in reader:
        print(row)


CSV WRITE
with open("data.csv","w",newline="") as f:
    writer = csv.writer(f)
    writer.writerow(["A","B"])


CSV APPEND
with open("data.csv","a",newline="") as f:
    writer = csv.writer(f)
    writer.writerow(["Bob",25])
```

### ⚡ MOST IMPORTANT DIFFERENCES

```text
sort()       → modifies original
sorted()     → new sorted list

L = L.sort() → ❌
L = sorted(L) → ✅


L2 = L       → reference
L2 = L.copy() → separate copy


L1 + L2      → concatenate
append(x)    → ONE item
extend(x)    → elements


max(L)       → maximum
min(L)       → minimum
count(x)     → how many
index(x)     → first position


"a" → append
"w" → overwrite
"x" → create only
"r" → read


read()       → whole file
read(n)      → n characters
readline()   → one line
for x in f   → line by line


os.remove()  → file
os.rmdir()   → folder


csv.reader() → read/parse CSV
csv.writer() → write CSV
writerow()   → write one row
next(reader) → skip/read header


LIST COMPREHENSION
if after for
→ FILTER

if ... else ... before for
→ CHANGE OUTPUT
```

