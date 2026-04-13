```c
#include<stdio.h>
int main(){
    int arr[]={9,4,7,1,3,5};
    int n=6;
    for(int i=1;i<n;i++){
        int key=arr[i];
       
        int j=i;
        while(j>0 && arr[j-1]>key){
            arr[j]=arr[j-1];
            j--;
        }
        arr[j]=key;


    }
    for(int i=0;i<n;i++){
        printf("%d ",arr[i]);
        
    }
}
```
# Insertion Sort

## Idea
Insertion Sort works like arranging playing cards in your hand.
👉 Take one element at a time and **insert it into its correct position** in the already sorted part of the array.

---
##  Algorithm Steps
1. Start from the second element (index 1)
2. Store current element as `key`
3. Compare it with elements on the left
4. Shift all elements greater than `key` to the right
5. Insert `key` at its correct position
6. Repeat until array is sorted
---
## Dry Run Example

### Initial Array:

```
9 4 7 1 3
```

---

### 🔹 Pass 1 (i = 1, key = 4)

Sorted part: `[9]`

* 9 > 4 → shift

```
9 9 7 1 3
```

Insert key:

```
4 9 7 1 3
```

---

### 🔹 Pass 2 (i = 2, key = 7)

Sorted part: `[4 9]`

* 9 > 7 → shift

```
4 9 9 1 3
```

Insert key:

```
4 7 9 1 3
```
---
### 🔹 Pass 3 (i = 3, key = 1)
Sorted part: `[4 7 9]`
* 9 > 1 → shift
* 7 > 1 → shift
* 4 > 1 → shift
```
4 4 7 9 3
```
Insert key:
```
1 4 7 9 3
```
---
### 🔹 Pass 4 (i = 4, key = 3)
Sorted part: `[1 4 7 9]`
* 9 > 3 → shift
* 7 > 3 → shift
* 4 > 3 → shift
```
1 4 4 7 9
```
Insert key:
```
1 3 4 7 9
```
---
## ✅ Final Output

```
1 3 4 7 9
```
---
## ⚡ Key Points
* Left side is always **sorted**
* Uses **shifting, not swapping**
* Works well for **small or nearly sorted arrays**
---
## ⏱️ Time Complexity

* Best Case: O(n)
* Worst Case: O(n²)
---

## 🔥 One-Line Summary

👉 **Pick element → shift larger elements → insert at correct position**
