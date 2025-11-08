1. ==**Syntax==**
	```c
# include <stdio.h>
int main() {
int marks[3];
printf("physics : ");
scanf("%d", &marks[0]);
printf("chem : ");
scanf("%d", &marks[1]);
printf("math : ");
scanf("%d", &marks[2]);
printf("physics = %d, ", marks[0]); //physics
printf("chem = %d, ", marks[1]); //chem
printf("math = %d \n", marks[2]); //math

return 0;
}
```
2. ==**Pointer Arithmetic==**
```c
# include <stdio.h>
int main() {
int age = 22;
int *ptr = &age;
int _age = 25;
int *_ptr = &_age;
printf("%u\n", ptr);
ptr++;
printf("%u\n", ptr);
ptr--;
printf("%u\n", ptr);
ptr = ptr - _ptr;
printf("%u\n", ptr);
ptr = &_age;
printf("%d\n", ptr == _ptr);
return 0;
}
```
3. ==**Accessing an Array==**
4. ```c
   # include <stdio.h>
void printNumbers(int *arr, int n);
void _printNumbers(int arr[], int n);
int main() {
     int arr[] = {1, 2, 3, 4, 5, 6};
     printNumbers(arr, 6);
     printNumbers(arr, 6);
     return 0;
    }

void printNumbers(int *arr, int n) {
    for(int i=0; i<n; i++) {
     printf("%d : %d\n", i, arr[i]);
     }
}
void _printNumbers(int arr[], int n) {
     for(int i=0; i<n; i++) {
     printf("%d : %d\n", i, arr[i]);
    }
}
   ```
4. ==**Build a 2D Array tables==**
```c
#include<stdio.h>
void exe(int arr[][10],int m , int n,int number);
int main(){
    int table[2][10];
    exe(table,0,10,3);
    exe(table,1,10,5);
     for(int i=1;i<=10;i++){    
        printf("%d\t ",table[0][i]);
    }
    printf("\n");
    for(int i=1;i<=10;i++){
      printf("%d\t",table[1][i]);
    }
    printf("\n");
    return 0;
  }
void exe(int arr[][10],int m,int n,int number){
     for(int i=1;i<=n;i++){
        arr[m][i]= number*i;
    }
}
```

5.==**Using Size of Array**==
```c
    int arr[] = {10, 55, 23, 89, 4, 72};
    int n = sizeof(arr) / sizeof(arr[0]);
```
