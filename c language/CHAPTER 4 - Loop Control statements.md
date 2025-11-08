==**For loop**== :-To print 0 to 10
```c
#include <stdio.h>
int main(){
     for(int i = 0 ;i<=10;i++){
        printf("%d\n",i);
    }
    return 0;
}
```
**==While Loop==** :- to print 1 to 5
```c
#include <stdio.h>
int main(){
    int i = 1;
    while(i<=5){
        printf("%d\n",i);
        i++;
    }
    return 0;
}
```
**==Do While Loop==** :- to print 1 to 100
```c
#include <stdio.h>
int main(){
   int i = 1;
   do {
       printf("%d\n", i);
       i++;
    } while(i<=100);
    return 0;
}
```
**==Using Break To End a Loop==**
```c
#include <stdio.h>
int main(){
     for(int i = 0 ;i<=5;i++){
            if(i==3){
               break;            //code wont run after 2
            }
            printf("%d\n",i);
     }
      return 0;  
}                            //result= 0,1,2
```                        
**==Using Continue to Skip a Part in Loop==**
```c
#include <stdio.h>
int main(){
     for(int i = 0 ;i<=5;i++){
            if(i==3){
               continue;           //skips 3
            }
            printf("%d\n",i);
     }
      return 0;
}                         //result= 0,1,2,4,5
```