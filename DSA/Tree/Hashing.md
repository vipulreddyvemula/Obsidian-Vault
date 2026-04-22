
## HASHING

### What is Hashing?

Hashing is a technique to store, delete, and find elements in **constant average time O(1)** using a hash function and hash table.

**Two main components:**

- **Hash Function h(k)** → formula that converts a key to an index
- **Hash Table** → array where data is actually stored

**Basic idea:**

```
Key  →  [Hash Function]  →  Index in Hash Table
1234 →     1234 % 10    →         4
```

---

### Hash Table

- An array of fixed size (TableSize)
- Each item has a **key** (e.g., roll number, name, ID)
- Key is mapped to index 0 to TableSize-1 using hash function
- Supports insertions, deletions, finds in **O(1) average**
- NOT efficient for operations needing order (findMin, findMax, sorted print)

---

### Hash Function

A good hash function must:

- Be **simple to compute**
- **Distribute keys evenly** across the table
- Minimize collisions

**Problems with hash functions:**

- Keys may not be numeric
- Number of possible keys >> table size
- Two different keys can map to same location → **Collision**

---

## Hash Function Methods

### (a) Division Method

**Formula:** `h(k) = k mod m`

- m should be a **prime number** larger than number of keys
- Most commonly used method

**Example:**

```
Elements: 3205, 7148, 2345
m = 97 (prime)

h(3205) = 3205 mod 97 = 4
h(7148) = 7148 mod 97 = 67
h(2345) = 2345 mod 97 = 17
→ No collisions!
```

**Why prime?** Prime numbers distribute keys more uniformly and reduce collisions.

---

### (b) Folding Method

**Idea:** Split key into parts → add the parts together → ignore last carry

**Formula:** `h(k) = k₁ + k₂ + ... + kₙ`

**Example:**

```
h(3205) = 32 + 05 = 37
h(7148) = 71 + 48 = 119 → ignore carry → 19
h(2345) = 23 + 45 = 68
```

---

### (c) Mid-Square Method

**Idea:** Square the key → delete digits from both ends → use middle digits

**Formula:** `h(k) = l` where l = middle digits of k²

**Note:** Same digit positions must be used for all keys

**Example:**

```
k:    3205          7148          2345
k²:   10272025      51093904      5499025
h(k): 72            93            99
(4th and 5th digits from right selected)
```

---

## Collision

**Definition:** When two different keys produce the same hash value (map to same index).

```
h(3205) = 5
h(2345) = 5   ← COLLISION! Both want index 5
```

**If too many collisions → performance drops drastically**

---

## Collision Resolution Methods

```
Collision Resolution
├── 1. Separate Chaining
└── 2. Open Addressing
         ├── Linear Probing
         ├── Quadratic Probing
         └── Double Hashing
```

---

### Method 1: Separate Chaining

**Idea:** Each index of the hash table holds a **linked list**. All elements that hash to the same index are stored in that list.

**How it works:**

- Array elements are pointers to first nodes of linked lists
- New item is inserted at the **front** of the list
- To search → go to index, traverse linked list

**Example:**

```
Keys: 0, 1, 4, 9, 16, 25, 36, 49, 64, 81
h(k) = k mod 10

Index 0 → [0] → NULL
Index 1 → [81] → [1] → NULL
Index 2 → NULL
Index 4 → [64] → [4] → NULL
Index 5 → [25] → NULL
Index 6 → [36] → [16] → NULL
Index 9 → [49] → [9] → NULL
```

**Advantages:**

- Better space utilization for large items
- Simple collision handling
- Can store MORE items than table size
- Deletion is quick and easy

**Disadvantage:**

- Requires extra memory for linked list pointers

---

### Method 2: Open Addressing

**Idea:** All data stays INSIDE the table (no linked lists). On collision → probe for next empty slot.

Requires a **bigger table** than the number of elements.

---

#### (a) Linear Probing

**Formula:** `(h(k) + i) mod TableSize` for i = 0, 1, 2, 3...

**How it works:**

- Check slot h(k). If occupied, check h(k)+1, h(k)+2, ...
- Wraps around using modulus if end of table reached
- Guaranteed to find empty slot if one exists

**Example:**

```
Keys: 89, 18, 49, 58, 9    h(k) = k mod 10

Insert 89: h(89)=9 → slot 9 empty       → placed at 9
Insert 18: h(18)=8 → slot 8 empty       → placed at 8
Insert 49: h(49)=9 → slot 9 taken!
           try (9+1)%10=0 → empty        → placed at 0
Insert 58: h(58)=8 → slot 8 taken!
           try 9 → taken, try 0 → taken
           try 1 → empty                 → placed at 1
Insert 9:  h(9)=9  → taken, probe...    → placed at 2

Final: [0]=49 [1]=58 [2]=9 [8]=18 [9]=89
```

**Deletion → Lazy Deletion:**

- Cannot physically remove an element
- Must **mark as DELETED** (not EMPTY)
- Why? If 89 is removed from index 9, searching for 9 would stop at index 9 (now EMPTY) and incorrectly say "not found"

**Problem — Primary Clustering:**

- Blocks of occupied cells start forming
- Any new key hashing into the cluster makes cluster bigger
- Slows down performance

---

#### (b) Quadratic Probing

**Formula:** `(h(k) + i²) mod TableSize` for i = 0, 1, 2, 3...

**How it works:**

- On collision, try positions h(k)+1², h(k)+2², h(k)+3²...
- Jumps are larger → avoids primary clustering

**Example:**

```
Keys: 89, 18, 49, 58, 9    h(k) = k mod 10

Insert 89: h(89)=9 → empty              → placed at 9
Insert 18: h(18)=8 → empty              → placed at 8
Insert 49: h(49)=9 → taken!
           try 9+1²=0 → empty           → placed at 0
Insert 58: h(58)=8 → taken!
           try 8+1²=9 → taken
           try 8+2²=12%10=2 → empty     → placed at 2
Insert 9:  h(9)=9  → taken!
           try 9+1²=0 → taken
           try 9+2²=13%10=3 → empty     → placed at 3

Final: [0]=49 [2]=58 [3]=9 [8]=18 [9]=89
```

**Solves:** Primary clustering ✅

**Problem — Secondary Clustering:**

- Elements hashing to the same location probe the SAME sequence of alternative cells
- Not as bad as primary clustering but still a problem

---

#### (c) Double Hashing

**Formula:** `(h(k) + i * g(k)) mod m`

Uses **two hash functions:**

```
h(k) = k mod m          ← first probe location
g(k) = q - (k mod q)   ← step size
```

Where q < m, and both m and q are **prime numbers**

**Why two functions?** Different keys get different step sizes → eliminates secondary clustering

**Example:**

```
m=11, q=7    h(k) = k mod 11    g(k) = 7-(k mod 7)
Keys: 2, 24, 46, 13

Insert 2:
  h(2)=2 → slot 2 empty → placed at 2

Insert 24:
  h(24)=2 → taken!
  g(24)=7-(24 mod 7)=7-3=4
  try (2+1×4)%11=6 → empty → placed at 6

Insert 46:
  h(46)=2 → taken!
  g(46)=7-(46 mod 7)=7-4=3
  try (2+1×3)%11=5 → empty → placed at 5

Insert 13:
  h(13)=2 → taken!
  g(13)=7-(13 mod 7)=7-6=1
  try (2+1×1)%11=3 → empty → placed at 3

Final: [2]=2  [3]=13  [5]=46  [6]=24
```

**Solves:** Both primary and secondary clustering ✅

---

## Full Collision Resolution Comparison

|Method|Probe Formula|Clustering|Notes|
|---|---|---|---|
|Separate Chaining|Linked list|None|Can exceed table size|
|Linear Probing|h(k)+i|Primary ❌|Simplest open addressing|
|Quadratic Probing|h(k)+i²|Secondary ❌|Better than linear|
|Double Hashing|h(k)+i·g(k)|None ✅|Best open addressing|

---

## Time Complexity of Hashing

|Operation|Average Case|Worst Case|
|---|---|---|
|Insert|O(1)|O(n)|
|Search|O(1)|O(n)|
|Delete|O(1)|O(n)|

**Comparison with other search methods:**

|Method|Average Time|
|---|---|
|Linear Search|O(n)|
|Binary Search|O(log n)|
|Hashing|**O(1)** ✅|

---

## Applications of Hashing

- **Compilers** → symbol tables to track declared variables
- **Game programs** → transposition tables to track positions
- **Spell checkers** → quickly look up whether a word exists
- **Databases** → fast record retrieval
- **Password storage** → storing hashed passwords

---

## Important Points for Exam 🎯

- Hash function must be simple and distribute keys evenly
- Division method → m must be a **prime number**
- Folding method → split key, add parts, ignore carry
- Mid-square → square key, extract middle digits
- Collision → two keys map to same index
- Separate chaining → uses linked lists, new item added at **front**
- Linear probing → primary clustering problem
- Quadratic probing → secondary clustering problem
- Double hashing → best, eliminates both clusterings
- **Lazy deletion** is mandatory in open addressing → mark as DELETED not EMPTY
- Build heap is O(n) ← common exam trick question
- Hashing does NOT support ordered operations like findMin, findMax, sort