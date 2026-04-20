#  Array Representation (VERY IMPORTANT)

👉 Heap is stored like this:
```
Index:   0   1   2   3   4   5   6  
Value:  10  20  15  30  40  50  100
```

For any index `i`:

- Left child → `2i + 1`
- Right child → `2i + 2`
- Parent → `(i-1)/2`
# Insertion (Min Heap)

##  Idea:

👉 Insert at end → **bubble up (heapify up)**
### Steps:

1. Insert at last
2. Compare with parent
3. Swap if smaller
4. Repeat
### Example:
Insert `5` into:
```
[10, 20, 15, 30]

Step:

[10, 20, 15, 30, 5]  
→ swap with 20  
→ swap with 10  
→ [5, 10, 15, 30, 20]
```

```c
void insert(int heap[], int* n, int val) {
    int i = (*n)++;
    heap[i] = val;

    while (i > 0 && heap[(i-1)/2] > heap[i]) {
        int temp = heap[i];
        heap[i] = heap[(i-1)/2];
        heap[(i-1)/2] = temp;
        i = (i-1)/2;
    }
}
```

## we need not to learn insert seperate as you can insert and perform heapify

---
## 2. MIN-HEAPIFY
```c
void heapify(int heap[], int n, int i) {
    int smallest = i;
    int left = 2*i + 1;
    int right = 2*i + 2;

    if (left < n && heap[left] < heap[smallest])
        smallest = left;

    if (right < n && heap[right] < heap[smallest])
        smallest = right;

    if (smallest != i) {
        int temp = heap[i];
        heap[i] = heap[smallest];
        heap[smallest] = temp;

        heapify(heap, n, smallest);
    }
}
```
---
# 3. Deletion (Min Heap)

Remove root (smallest)
### Steps:

1. Replace root with last element
2. Delete last
3. **Heapify down**
### Example:
```
[5, 10, 15, 30, 20]
→ remove 5
→ [20, 10, 15, 30]
→ swap with 10
→ [10, 20, 15, 30]
```

### TO convert a Array to heap
Start from **last non-leaf node**
Last non-leaf = (n/2) - 1
```c
for (int i = n/2 - 1; i >= 0; i--) {
    heapify(arr, n, i);
}
```
