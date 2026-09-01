```c
#include<stdio.h>
void swap(int *a,int *b){
    int temp=*a;
    *a=*b;
    *b=temp;
}
int partition(int arr[],int left,int right){
    int pivot=arr[right];
    int x=left;
    for(int i=left;i<right;i++){
        if(arr[i]<=pivot){
            swap(&arr[x],&arr[i]);
            x++;
        }
    }
    swap(&arr[x],&arr[right]);
    return x;

}
void quicksort(int arr[],int left,int right){
    if(left<right){
        int pivotindex=partition(arr,left,right);
        quicksort(arr,left,pivotindex-1);
        quicksort(arr,pivotindex+1,right);
        [[Quick Sort]]
    }

}
int main(){

}
```

#


#  Quick Sort – Simple Explanation + Dry Run

## 🔹 swap()

```c
void swap(int *a,int *b)
```

* Exchanges two values using pointers
* Used during partitioning

---

## 🔹 partition()

```c
int partition(int arr[],int left,int right)
```

👉 This is the core of Quick Sort

* Picks the last element as pivot:

```c
int pivot = arr[right];
```

* Rearranges array so:

  * All elements ≤ pivot go left
  * All elements > pivot go right

---

## 🔹 How it works:

* `x` → position where next smaller element should go
* Loop from `left → right-1`

```c
if(arr[i] <= pivot)
```

* Swap current element with `arr[x]`
* Move `x++`

Finally:

```c
swap(&arr[x], &arr[right]);
```

👉 Places pivot in correct sorted position

---

## 🔹 quicksort()

```c
void quicksort(int arr[],int left,int right)
```

* Recursively sorts:

  * Left side of pivot
  * Right side of pivot

---

# 🔍 Dry Run Example

## Input:

```
[9, 3, 7, 1, 6]
```

---

## 🧩 Step 1: First Call

```
quicksort(arr, 0, 4)
pivot = 6
```

### Partition Process:

| i | arr[i] | Action                         |
| - | ------ | ------------------------------ |
| 0 | 9      | skip                           |
| 1 | 3      | swap with arr[0] → [3,9,7,1,6] |
| 2 | 7      | skip    \
                       |
| 3 | 1      | swap with arr[1] → [3,1,7,9,6] |

Now:

```
swap(arr[2], arr[4])
```

👉 Result:

```
[3, 1, 6, 9, 7]
pivot index = 2
```

---

## 🧩 Step 2: Left Side

```
[3,1]
pivot = 1
```

After partition:

```
[1,3]
```

---

## 🧩 Step 3: Right Side

```
[9,7]
pivot = 7
```

After partition:

```
[7,9]
```

---

## ✅ Final Sorted Array:

```
[1, 3, 6, 7, 9]
```

---

# ⚠️ Important Observations

## ❗ Worst Case

Already sorted array:

```
[1,2,3,4,5]
```

👉 Time Complexity becomes **O(n²)**

---

## ❗ Pivot Choice Matters

You always use:

```c
pivot = arr[right]
```

👉 Can be inefficient for:

* Sorted arrays
* Reverse sorted arrays
