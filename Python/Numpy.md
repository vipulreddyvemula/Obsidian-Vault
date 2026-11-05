# NumPy 

## Import

```
import numpy as np
```

## 1. Array creation

```
a = np.array([1, 2, 3])           # 1D array
b = np.array([[1, 2], [3, 4]])    # 2D array

np.zeros((2, 3))       # 2x3 zeros
np.ones((2, 3))        # 2x3 ones
np.eye(3)              # 3x3 identity matrix
np.arange(1, 10, 2)    # [1, 3, 5, 7, 9]
np.linspace(0, 10, 5)  # 5 equally spaced values
```

`arange(start, stop, step)` — stop excluded.

`linspace(start, stop, num)` — endpoints included by default.

## 2. Array properties

```
a.ndim      # Number of dimensions
a.shape     # Shape (rows, columns)
a.size      # Total elements
a.dtype     # Data type
a.T         # Transpose
```

## 3. Reshape

```
a = np.arange(6)
b = a.reshape(2, 3)

# [[0 1 2]
#  [3 4 5]]
```

Number of elements must match.

## 4. Array indexing and slicing

```
a[0]         # First element/row
a[-1]        # Last element/row
a[1:4]       # Indices 1, 2, 3
a[0, 1]      # Row 0, column 1
a[:, 0]      # First column
a[0, :]      # First row
a[-2, :]     # Second-last row
```

## 5. Mathematical operations

```
A + B             # Element-wise addition
A - B             # Element-wise subtraction
A * B             # Element-wise multiplication
A / B             # Element-wise division

np.dot(A, B)      # Matrix multiplication
A @ B             # Matrix multiplication
A.T               # Transpose

np.linalg.det(A)  # Determinant
np.linalg.inv(A)  # Inverse
```

## 6. Statistical operations

```
np.sum(a)         # Sum of all elements
np.mean(a)        # Mean
np.median(a)      # Median
np.std(a)         # Standard deviation
np.min(a)         # Minimum
np.max(a)         # Maximum
np.sort(a)        # Sort values
np.argmax(a)      # Index of maximum
np.argmin(a)      # Index of minimum
```

## 7. Axis — Very Important

```
np.sum(a, axis=0)    # Column sums
np.sum(a, axis=1)    # Row sums

np.sort(a, axis=0)   # Sort each column
np.sort(a, axis=1)   # Sort each row
```

**Remember:** `axis=0` operates down rows (column-wise); `axis=1` operates across columns (row-wise).

## 8. Random

```
np.random.randint(1, 10)                 # Integer 1–9
np.random.randint(1, 100, size=(5, 5))   # 5x5 matrix
np.random.rand(3, 3)                     # Random floats, 3x3
np.random.choice([1, 2, 3])              # Random selection
```

## 9. Copy vs View

```
b = a.copy()   # Independent data
b = a.view()   # Shares underlying data
```

Changing elements through a view can change the original array.

## 10. Joining arrays

```
np.concatenate((a, b))
np.vstack((a, b))    # Stack vertically
np.hstack((a, b))    # Stack horizontally
```

## Important PYQ syntax

**November 2023 End Sem — Q10(b): Second-largest in each column**

```
a = np.random.randint(1, 100, (5, 5))
result = np.sort(a, axis=0)[-2, :]
print(result)
```

**February 2023 End Sem — Q8(a): Matrix sums**

```
print(np.sum(a))          # Total
print(np.sum(a, axis=1))  # Each row
print(np.sum(a, axis=0))  # Each column
```

**November 2024 End Sem — Q9: Extract five digits and reshape**

```
s = input()
digits = [int(c) for c in s if c.isdigit()]

if len(digits) == 5:
    print(np.array(digits).reshape(5, 1))
else:
    print("Invalid number of digits")
```

## Memory Tricks

- `shape` → Dimensions' sizes
    
- `ndim` → Number of dimensions
    
- `size` → Total elements
    
- `reshape(r,c)` → Convert shape
    
- `*` → Element-wise multiplication
    
- `@` → Matrix multiplication
    
- `axis=0` → Column-wise
    
- `axis=1` → Row-wise
    
- `[-2, :]` → Second-last row