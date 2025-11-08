==**If-Else statements**==    for pass marks>30
```c
# include<stdio.h>
int main() {
    int marks;
    printf("Enter your marks:");
    scanf("%d", &marks );
    if (marks>30){
    printf("pass");
    }
    else {
    printf("fail");
    }
    return 0;
}
```

**==Ternary Operator==** **imp
```c
# include<stdio.h>
int main() {
    int marks;
    printf("Enter your marks:");
    scanf("%d", &marks );
    marks>30 ? printf("pass"):printf("Fail");
    return 0;
}
```
==**Switch (integer)**==
```c
#include<stdio.h>
#include<math.h>
int main() {
int day = 5;
switch(day) {
case 1 : printf("monday \n");
break;
case 2 : printf("tuesday \n");
break;
}
return 0;
}
```
==**Switch (character)**==
```c
#include<stdio.h>
#include<math.h>
    int main() { 
    char day = 'f';
    switch(day) {
    case 'm' : printf("monday \n");
    break;case 'S' : printf("sunday \n");
    break;
    }
return 0;
}
```
