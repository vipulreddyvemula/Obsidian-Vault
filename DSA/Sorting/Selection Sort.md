```c
#include <stdio.h>

int main(){
    int arr[] = {9, 4, 7, 1, 3};
    int n = 5;

    for(int i = 0; i < n-1; i++){
        int minIndex = i;

        for(int j = i+1; j < n; j++){
            if(arr[j] < arr[minIndex]){
                minIndex = j;
            }
        }

        // swap
        int temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;
    }

    for(int i = 0; i < n; i++){
        printf("%d ", arr[i]);
    }

    return 0;
}
```
## Dry Run (STEP BY STEP)

Initial:

9 4 7 1 3
## 🔹 Pass 1 (i = 0)

Find minimum in:

[9 4 7 1 3]

👉 min = **1 (index 3)**

Swap with index 0:

1 4 7 9 3

---

## 🔹 Pass 2 (i = 1)

Find minimum in:

[4 7 9 3]

👉 min = **3 (index 4)**

Swap:

1 3 7 9 4

---

## 🔹 Pass 3 (i = 2)

Find minimum in:

[7 9 4]

👉 min = **4 (index 4)**

Swap:

1 3 4 9 7

---

## 🔹 Pass 4 (i = 3)

Find minimum in:

[9 7]

👉 min = **7 (index 4)**

Swap:

1 3 4 7 9

---

# ✅ Final Output

1 3 4 7 9