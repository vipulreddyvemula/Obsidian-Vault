```c
#include<stdio.h>
void merge(int arr[],int left,int m,int right){
    int left_length=m-left+1;
    int right_length=right-m;
    int leftarray[left_length];
    int rightarray[right_length];
    for(int i=0;i<left_length;i++){
	        leftarray[i]=arr[left+i];
    }
    for(int i=0;i<right_length;i++){
        rightarray[i]=arr[m+1+i];
    }
    int i=0;
    int j=0;
    int k=left;
    while (i < left_length && j < right_length) {
        if (leftarray[i] <= rightarray[j]) {
            arr[k++] = leftarray[i++];
        } else {
            arr[k++] = rightarray[j++];
        }
    }

    // Copy remaining elements
    while (i < left_length) {
        arr[k++] = leftarray[i++];
    }

    while (j < right_length) {
        arr[k++] = rightarray[j++];
    }


}
void mergesort(int arr[],int left,int right){
    if(left<right){
        int mid=left+(right-left)/2;
        mergesort(arr,left,mid);
        mergesort(arr,mid+1,right);
        merge(arr,left,mid,right);
    }
   

}
int main(){
    // test array and length
  int array[] = { 9, 4, 8, 1, 7, 0, 3, 2, 5, 6};
  int length = 10;
  
  // sort the array using merge sort
  mergesort(array, 0,length-1);
  
  // print out the array elements to verify they have been sorted
  for (int i = 0; i < length; i++)
    printf("%d ", array[i]);
  printf("\n");
  
  return 0;

}
```
---

## Dry Run — `arr = {5, 3, 8, 1, 4}`

### Phase 1 — Splitting (Recursive Calls)

```
mergeSort(arr, 0, 4)               → mid = 2
├── mergeSort(arr, 0, 2)           → mid = 1
│   ├── mergeSort(arr, 0, 1)       → mid = 0
│   │   ├── mergeSort(arr, 0, 0)   → [5]  ✅ base case
│   │   └── mergeSort(arr, 1, 1)   → [3]  ✅ base case
│   │   └── merge(0, 0, 1)         → merges [5] and [3]
│   └── mergeSort(arr, 2, 2)       → [8]  ✅ base case
│   └── merge(0, 1, 2)             → merges [3,5] and [8]
└── mergeSort(arr, 3, 4)           → mid = 3
    ├── mergeSort(arr, 3, 3)       → [1]  ✅ base case
    └── mergeSort(arr, 4, 4)       → [4]  ✅ base case
    └── merge(3, 3, 4)             → merges [1] and [4]

mergeSort done → merge(0, 2, 4)    → merges [3,5,8] and [1,4]
```

---

]### Phase 2 — Merging (Step by Step)

**Step 1:** `merge([5], [3])` → indices 0–1

```
L = [5],  R = [3]
3 < 5  → take 3
5 left → take 5
Result: arr[0..1] = [3, 5]
```

**Step 2:** `merge([3,5], [8])` → indices 0–2

```
L = [3, 5],  R = [8]
3 < 8  → take 3
5 < 8  → take 5
8 left → take 8
Result: arr[0..2] = [3, 5, 8]
```

**Step 3:** `merge([1], [4])` → indices 3–4

```
L = [1],  R = [4]
1 < 4  → take 1
4 left → take 4
Result: arr[3..4] = [1, 4]
```

**Step 4 (Final):** `merge([3,5,8], [1,4])` → indices 0–4

```
L = [3, 5, 8],  R = [1, 4]

i=0, j=0 → 1 < 3  → take 1    → [1]
i=0, j=1 → 3 < 4  → take 3    → [1, 3]
i=1, j=1 → 4 < 5  → take 4    → [1, 3, 4]
i=1, j=2 → 5, no R left → take 5  → [1, 3, 4, 5]
i=2, j=2 → 8, no R left → take 8  → [1, 3, 4, 5, 8]

Result: arr[0..4] = [1, 3, 4, 5, 8] ✅
```

---

### Final Output

```
Original array: 5 3 8 1 4
Sorted array:   1 3 4 5 8
```