# SciPy 
SciPy is used for scientific computing, mathematical algorithms, constants, sparse matrices and graph operations.

## 1. Import scientific constants

```
from scipy import constants
```

```
constants.minute   # 60 seconds
constants.hour     # 3600 seconds
constants.day      # 86400 seconds
constants.gram     # 0.001 kilograms
constants.pi       # Pi
```

## 2. Sparse matrix

Sparse matrix = Matrix containing mostly zeros.

```
import numpy as np
from scipy.sparse import csr_matrix

a = np.array([
    [0, 1, 0],
    [1, 0, 0],
    [0, 0, 0]
])

graph = csr_matrix(a)
```

`csr_matrix()` converts a regular matrix to Compressed Sparse Row format.

## 3. Connected Components — Important faculty example

```
import numpy as np
from scipy.sparse import csr_matrix
from scipy.sparse.csgraph import connected_components

a = np.array([
    [0, 1, 0],
    [1, 0, 0],
    [0, 0, 0]
])

graph = csr_matrix(a)

count, labels = connected_components(
    graph, directed=False
)

print(count)
print(labels)
```

Output:

```
2
[0 0 1]
```

Explanation:

- Nodes 0 and 1 are connected.
    
- Node 2 is isolated.
    
- Total components = 2.
    

## 4. Key syntax

```
csr_matrix(a)                # Create sparse matrix

connected_components(
    graph,
    directed=False
)
```

`directed=False` treats the graph as undirected.

Return values:

- `count` → Number of connected components
    
- `labels` → Component ID for every node
    

## Memory Tricks

- `constants` → Scientific values
    
- `csr_matrix()` → Sparse representation
    
- `connected_components()` → Find connected groups
    
- `directed=False` → Undirected graph
    

**Faculty slides 49–52.** No direct SciPy question identified in the uploaded November 2025 paper.