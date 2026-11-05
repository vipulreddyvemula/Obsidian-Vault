# 🐍 Python List — Tiny Cheat Sheet

## List Slicing ⭐

**Syntax:**

```python
L[start:end:step]
```

|Syntax|Meaning|Example|Output|
|---|---|---|---|
|`L[2:5]`|index 2 → 4|`[1,2,3,4,5,6][2:5]`|`[3,4,5]`|
|`L[:4]`|start → index 3|`[1,2,3,4,5][:4]`|`[1,2,3,4]`|
|`L[2:]`|index 2 → end|`[1,2,3,4,5][2:]`|`[3,4,5]`|
|`L[:]`|whole list/copy|`[1,2,3][:]`|`[1,2,3]`|
|`L[::2]`|every 2nd element|`[1,2,3,4,5][::2]`|`[1,3,5]`|
|`L[::3]`|every 3rd element|`[1,2,3,4,5,6][::3]`|`[1,4]`|
|`L[::-1]`|reverse|`[1,2,3][::-1]`|`[3,2,1]`|
|`L[::-2]`|reverse, every 2nd|`[1,2,3,4,5][::-2]`|`[5,3,1]`|
|`L[-4:-1]`|negative-index slice|`[1,2,3,4,5][-4:-1]`|`[2,3,4]`|

**Remember:** `start` ✅ included, `end` ❌ excluded.

---

# ⭐⭐⭐ MASTER TABLE — List Methods

|Method|Syntax|Meaning|Example|Output|
|---|---|---|---|---|
|`append()`|`L.append(x)`|Add **ONE item** at end|`L=[1,2]; L.append(3)`|`[1,2,3]`|
|`clear()`|`L.clear()`|Empty list|`L=[1,2]; L.clear()`|`[]`|
|`copy()`|`L.copy()`|Create separate copy|`L=[1,2]; M=L.copy()`|`M → [1,2]`|
|`count()`|`L.count(x)`|Count occurrences of `x`|`L=[1,2,2,3]; L.count(2)`|`2`|
|`extend()`|`L.extend(iterable)`|Add iterable's elements|`L=[1,2]; L.extend([3,4])`|`[1,2,3,4]`|
|`index()`|`L.index(x)`|First index of `x`|`L=[10,20,30]; L.index(20)`|`1`|
|`insert()`|`L.insert(i,x)`|Insert `x` at index `i`|`L=[1,3]; L.insert(1,2)`|`[1,2,3]`|
|`pop(i)`|`L.pop(i)`|Remove item at index `i`|`L=[1,2,3]; L.pop(1)`|`[1,3]`|
|`pop()`|`L.pop()`|Remove **last** item|`L=[1,2,3]; L.pop()`|`[1,2]`|
|`remove()`|`L.remove(x)`|Remove **first occurrence of value**|`L=[1,2,2,3]; L.remove(2)`|`[1,2,3]`|
|`reverse()`|`L.reverse()`|Flip current order|`L=[1,2,3]; L.reverse()`|`[3,2,1]`|
|`sort()`|`L.sort()`|Sort ascending|`L=[3,1,2]; L.sort()`|`[1,2,3]`|
|`sort(reverse=True)`|`L.sort(reverse=True)`|Sort descending|`L=[3,1,2]; L.sort(reverse=True)`|`[3,2,1]`|
|`sort(key=str.lower)`|`L.sort(key=str.lower)`|Case-insensitive sort|`L=["banana","Orange","Kiwi"]`|`['banana','Kiwi','Orange']`|
|`sort(key=str.lower, reverse=True)`|`L.sort(key=str.lower, reverse=True)`|Case-insensitive descending|`L=["banana","Orange","Kiwi"]`|`['Orange','Kiwi','banana']`|

---

# 🔥 MASTER CHEAT

```text
SLICE
L[s:e:step]
s = included
e = excluded

L[2:5]        → index 2 to 4
L[:5]         → beginning to index 4
L[2:]         → index 2 to end
L[:]          → copy
L[::2]        → every 2nd
L[::3]        → every 3rd
L[::-1]       → reverse
L[::-2]       → reverse every 2nd
L[-4:-1]      → negative slicing


METHODS
append(x)                        → add ONE item at end
clear()                          → empty list
copy()                           → copy list
count(x)                         → count x
extend(iterable)                 → add elements
index(x)                         → first index
insert(i,x)                      → insert at i
pop(i)                           → remove index i
pop()                            → remove LAST
remove(x)                        → remove first x
reverse()                        → reverse current order
sort()                           → ascending
sort(reverse=True)               → descending
sort(key=str.lower)              → case-insensitive
sort(key=str.lower,reverse=True) → case-insensitive descending
```

### ⚡ Most Important Differences

```text
append(x)       → ONE item
extend(x)       → multiple elements

append([4,5])   → adds [4,5] as ONE item
extend([4,5])   → adds 4 and 5 separately

remove(x)       → by VALUE
pop(i)          → by INDEX
pop()           → LAST

clear()         → empty list []
del L[i]        → delete by INDEX
del L           → delete entire list

copy()          → separate list
L[:]            → separate list

sort()          → arrange elements
reverse()       → simply flip existing order

sort(reverse=True)
→ descending

sort(key=str.lower)
→ case-insensitive ascending
```

---

### 6. Adding Elements

```python
L.append(x)                # ONE item at end
L.insert(i, x)             # item at index i
L.extend(iterable)         # elements of iterable at end
```

```python
L = [1,2,3]

L.append(4)
# [1,2,3,4]

L.insert(1,9)
# [1,9,2,3,4]

L.extend([5,6])
# [1,9,2,3,4,5,6]
```

`extend()` works with lists, tuples, sets, dictionaries, etc.

### Remember

```python
L.append([4,5])    # adds [4,5] as ONE item
L.extend([4,5])    # adds 4 and 5 separately
```

---

### 7. Removing Elements

```python
L.remove(x)          # remove first occurrence of VALUE
L.pop(i)             # remove INDEX i
L.pop()              # remove LAST
del L[i]             # delete INDEX i
del L                # delete entire list
L.clear()            # empty list
```

```python
L = [10,20,30,20]

L.remove(20)         # [10,30,20]
L.pop(1)             # removes index 1
L.pop()              # removes last
del L[0]             # deletes index 0
L.clear()            # []
```

`pop()` on empty list → `IndexError`.

### `del` vs `clear`

```text
del L       → L no longer exists
L.clear()   → L exists but becomes []
```

---

### 8. Searching / Information

```python
len(L)              # number of elements
L.index(x)           # first index of x
L.count(x)           # occurrences of x
```

Example:

```python
L = [10,20,20,30]

len(L)               # 4
L.index(20)          # 1
L.count(20)          # 2
```

---

### 9. Copying

```python
L2 = L.copy()
L2 = L[:]
```

Both create a separate list containing the same elements.

---

# 10. Sorting ⭐⭐⭐

```python
L.sort()                             # ascending
L.sort(reverse=True)                 # descending
L.sort(key=str.lower)                # case-insensitive ascending
L.sort(key=str.lower, reverse=True)  # case-insensitive descending
```

### Numeric

```python
L = [100,50,65,82,23]

L.sort()
# [23,50,65,82,100]

L.sort(reverse=True)
# [100,82,65,50,23]
```

### String

```python
L = ["orange","mango","kiwi","banana"]

L.sort()
# ['banana','kiwi','mango','orange']
```

### Case-insensitive

```python
L = ["banana","Orange","Kiwi","cherry"]

L.sort(key=str.lower)
# ['banana','cherry','Kiwi','Orange']
```

`sort()` is case-sensitive by default; `key=str.lower` makes comparison case-insensitive.

---

# 11. `sort()` vs `reverse()` ⭐

```python
L.sort()
```

→ **arranges** elements.

```python
L.reverse()
```

→ **flips existing order**.

```python
L = [3,1,2]

L.reverse()       # [2,1,3]
L.sort()          # [1,2,3]
```

---

# 12. List Operators

```python
len(L)             # length
L1 + L2            # concatenation
L * n              # repetition
x in L             # membership
```

```python
[1,2] + [3,4]
# [1,2,3,4]

[1,2] * 3
# [1,2,1,2,1,2]

2 in [1,2,3]
# True
```

---

# 13. Changing Elements

```python
L[i] = x                  # change one
L[start:end] = [...]      # replace range
```

```python
L = ["a","b","c"]

L[1] = "x"
# ["a","x","c"]

L[1:3] = ["x","y"]
# ["a","x","y"]
```

If replacement count ≠ selected range count:

- **more values** → list grows
    
- **fewer values** → list shrinks.