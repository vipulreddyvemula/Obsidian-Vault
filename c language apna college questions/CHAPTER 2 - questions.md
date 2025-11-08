1 ) TO CHECK IF A NUMBER IS EVEN OR ODD,OR DIVISIBLE BY 2
```c
#include<stdio.h>
int main() {
    int num;
    printf("Enter a number:");
    scanf("%d",&num);
    int num1 = num%2;
    printf("%d",num1==0);
    return 0;
}
```
