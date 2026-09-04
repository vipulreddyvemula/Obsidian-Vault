# 🐍 Week 4 — Tiny Cheat Sheet

### Tuples + Sets

---

# 1. Tuple Creation ⭐

|Syntax|Meaning|Example|Output|
|---|---|---|---|
|`T = (a,b,c)`|Create tuple|`T=("apple","banana","cherry")`|`('apple','banana','cherry')`|
|`T = ()`|Empty tuple|`T=()`|`()`|
|`T = (x,)`|**One-item tuple**|`T=("apple",)`|`('apple',)`|
|`T = x, y, z`|Parentheses optional|`T=1,2,3`|`(1,2,3)`|
|`tuple(L)`|Convert iterable/list → tuple|`tuple([1,2,3])`|`(1,2,3)`|

⭐ **One item needs comma:**

```python
("apple")   → str
("apple",)  → tuple
```

---

# 2. Tuple Slicing ⭐

### Syntax

```text
T[start:end:step]
```

|Syntax|Meaning|Example|
|---|---|---|
|`T[2:5]`|2 → 4|`('cherry','orange','kiwi')`|
|`T[:4]`|beginning → 3|first 4 items|
|`T[2:]`|2 → end|from index 2|
|`T[:]`|whole tuple|copy of tuple|
|`T[-1]`|last item|last value|
|`T[:-1]`|all except last|—|

```text
start → included
end   → excluded
```

---

# 3. Tuple Checking ⭐

```python
if "apple" in T:
    print("Yes")
```

```text
"x in T"
→ True  → item exists
→ False → item doesn't exist
```

---

# 4. Tuple Methods ⭐⭐⭐

|Method|Syntax|Meaning|Example → Output|
|---|---|---|---|
|`count()`|`T.count(x)`|Count occurrences|`(1,2,2,3).count(2)` → `2`|
|`index()`|`T.index(x)`|First position of x|`(1,3,7,8).index(8)` → `3`|

---

# 5. Change a Tuple ⭐

❌ Direct modification:

```python
T[1] = "kiwi"
```

→ **Not allowed** because tuple is immutable.

### Workaround

```python
T = ("apple","banana","cherry")

L = list(T)
L[1] = "kiwi"
T = tuple(L)

# ('apple','kiwi','cherry')
```

---

# 6. Add to Tuple ⭐

### Method 1 — List conversion

```python
T = ("apple","banana","cherry")

L = list(T)
L.append("orange")
T = tuple(L)

# ('apple','banana','cherry','orange')
```

### Method 2 — Tuple concatenation

```python
T = ("apple","banana","cherry")
x = ("orange",)

T += x

# ('apple','banana','cherry','orange')
```

```text
T += x
→ creates a NEW tuple
→ does NOT modify tuple in-place
```

---

# 7. Remove from Tuple

```python
T = ("apple","banana","cherry")

L = list(T)
L.remove("apple")
T = tuple(L)

# ('banana','cherry')
```

```text
Tuple → list → modify → tuple
```

---

# 8. Delete Tuple

```python
del T
```

```text
del T
→ deletes ENTIRE tuple

print(T)
→ NameError
```

---

# 9. Tuple Unpacking ⭐⭐⭐

```python
fruits = ("apple","banana","cherry")

(a,b,c) = fruits
```

```text
a → apple
b → banana
c → cherry
```

### With `*`

```python
fruits = ("apple","banana","cherry","strawberry")

(a,b,*c) = fruits

# a → apple
# b → banana
# c → ['cherry','strawberry']
```

### `*` in middle

```python
(a,*b,c) = fruits
```

```text
a → first
b → middle values (LIST)
c → last
```

---

# 10. Tuple Loops

### Direct

```python
for x in T:
    print(x)
```

### Using index

```python
for i in range(len(T)):
    print(T[i])
```

### Using while

```python
i = 0
while i < len(T):
    print(T[i])
    i += 1
```

---

# 11. Join & Repeat Tuples

### Join

```python
T1 = ("a","b","c")
T2 = (1,2,3)

T3 = T1 + T2

# ('a','b','c',1,2,3)
```

### Repeat

```python
T = ("apple","banana","cherry")

T2 = T * 2

# ('apple','banana','cherry',
#  'apple','banana','cherry')
```

---

# 🔥 TUPLE MASTER CHEAT

```text
CREATE
T = (1,2,3)
T = ()
T = (1,)
T = 1,2,3
tuple(L) → list → tuple


IMMUTABLE
❌ T[1] = x
❌ T.append()
❌ T.remove()

WORKAROUND
T → list(T) → modify → tuple(L)


ACCESS
T[i]
T[-1] → last


SLICE
T[s:e:step]
s → included
e → excluded

T[2:5]
T[:4]
T[2:]
T[:]


CHECK
x in T → True/False


METHODS
T.count(x) → occurrences
T.index(x) → first position


ADD
T += (x,)

→ creates new tuple


DELETE
del T → delete entire tuple


UNPACK
(a,b,c) = T

(a,b,*c) = T
→ c gets remaining values as LIST

(a,*b,c) = T
→ b gets middle values as LIST


JOIN
T1 + T2 → concatenate

REPEAT
T * n → repeat n times


LOOP
for x in T:
    ...

for i in range(len(T)):
    print(T[i])

while i < len(T):
    ...
```

---

# 🟢 SETS

## 12. Set Creation ⭐

```python
S = {"apple","banana","cherry"}
```

```text
{} → set with elements
set() → empty set
```

### Important properties

```text
unordered
unindexed
no duplicates
items themselves are immutable/hashable
set itself is mutable
```

Sets **cannot** be accessed using an index/key.

---

# 13. Set Duplicates

```python
S = {"apple","banana","cherry","apple"}

# {'apple','banana','cherry'}
```

```text
Duplicate values → automatically ignored
```

---

# 14. Set Data Types ⭐

```python
S = {"abc", 34, True, 40, "male"}
```

Allowed:

```text
int
float
str
bool
tuple (if its contents are immutable)
```

❌ Not allowed:

```text
list
dict
set
```

because these are mutable/unhashable.

---

# 15. `set()` Constructor

```python
S = set(("apple","banana","cherry"))
```

```text
set(iterable)
→ converts iterable to set
```

### From list

```python
set(["apple","banana","apple"])

# {'apple','banana'}
```

### From string

```python
set("banana")

# {'b','a','n'}
```

⚠️ `set()` accepts **one iterable argument**:

```python
set("apple","banana")  # ❌ TypeError
```

---

# 16. Access / Check Set ⭐

❌ No:

```python
S[0]
```

✅ Loop:

```python
for x in S:
    print(x)
```

✅ Check:

```python
"banana" in S
# True
```

---

# 17. Set Methods ⭐⭐⭐

|Method|Syntax|Meaning|Example|
|---|---|---|---|
|`add()`|`S.add(x)`|Add **one** item|`S.add("orange")`|
|`update()`|`S.update(iterable)`|Add multiple items|`S.update(["kiwi","orange"])`|
|`remove()`|`S.remove(x)`|Remove x; error if absent|`S.remove("banana")`|
|`discard()`|`S.discard(x)`|Remove x; **no error** if absent|`S.discard("banana")`|
|`pop()`|`S.pop()`|Remove & return arbitrary item|`x=S.pop()`|
|`clear()`|`S.clear()`|Empty set|`S → set()`|

---

# 18. `add()` vs `update()` ⭐⭐⭐

```python
S.add("orange")
```

```text
add()
→ ONE item only
```

```python
S.update(["kiwi","orange"])
```

```text
update()
→ MULTIPLE items
→ accepts any iterable
→ list / tuple / set / dictionary etc.
```

⚠️

```python
S.add("kiwi","grape")
# ❌ TypeError
```

---

# 19. `remove()` vs `discard()` ⭐⭐⭐

```python
S.remove("banana")
```

```text
item exists    → removes
item absent    → ❌ Error
```

```python
S.discard("banana")
```

```text
item exists    → removes
item absent    → ✅ No error
```

---

# 20. `pop()` in Set ⚠️

```python
x = S.pop()
```

```text
→ removes an arbitrary item
→ returns removed item
```

Because a set is unordered, **you cannot predict which item will be removed**.

---

# 21. `clear()` vs `del`

### `clear()`

```python
S.clear()
```

```text
→ removes all items
→ S still exists
→ empty set = set()
```

### `del`

```python
del S
```

```text
→ deletes entire set
→ S no longer exists
```

---

# 🔥🔥 SET MASTER CHEAT

```text
CREATE
S = {1,2,3}
set(iterable)
set() → empty set


PROPERTIES
unordered
unindexed
no duplicates

S itself → mutable
S items → must be immutable/hashable


ACCESS
S[0] → ❌

for x in S:
    ...

x in S → True/False


METHODS
add(x)
→ add ONE item

update(iterable)
→ add MULTIPLE items

remove(x)
→ remove x
→ error if x absent

discard(x)
→ remove x
→ NO error if x absent

pop()
→ remove + return arbitrary item

clear()
→ empty set

del S
→ delete entire set


CONVERSION
set([1,2,2,3])
→ {1,2,3}

set("banana")
→ {'b','a','n'}


ALLOWED
int
float
str
bool
immutable tuple

NOT ALLOWED
list ❌
dict ❌
set ❌
```

---

# ⚡ FINAL EXAM DIFFERENCES

```text
TUPLE
(1,2,3)
→ ordered
→ indexed
→ immutable
→ duplicates allowed


SET
{1,2,3}
→ unordered
→ unindexed
→ set is mutable
→ duplicate values NOT allowed


TUPLE
T.count(x)   → count
T.index(x)   → first position


SET
S.add(x)     → ONE
S.update(x)  → MANY

S.remove(x)  → error if absent
S.discard(x) → no error if absent

S.pop()      → arbitrary item
S.clear()    → empty
del S        → delete set


ONE-ITEM TUPLE
("a")  → string
("a",) → tuple


UNPACKING
(a,b,c) = T

(a,b,*c) = T
→ c = remaining values as LIST

(a,*b,c) = T
→ b = middle values as LIST
```

The **last pages of the PDF specifically emphasize the important distinction**: set membership can be changed with `add/remove/clear`, but individual set items must themselves be immutable/hashable.