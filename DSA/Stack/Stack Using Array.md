```cpp
#include<stdio.h>
#define MAX 5
int stack[MAX];
int top=-1;
void push(int x){
    if(top==MAX-1){
        printf("Stack overflow...");
    }
    else{
        stack[++top]=x;
    }
}
int pop(){
    if(top==-1){
        printf("Stack Underflow...");
        return -1;
    }
    else{
        return stack[top--];
    }
}
int peek(){
    if(top==-1){
        printf("Stack is empty");
        return -1;

    }
    else{
        return stack[top];
    }
}

int main(){
    printf("Enter Numbers: ");
    for(int i=0;i<MAX;i++){
        int n;
        scanf("%d",&n);
        push(n);
    }
    printf("Top element: %d\n", peek());
    printf("Popped: %d\n", pop());
    printf("Top element: %d\n", peek());

   //OUTPUT:-  
   %% Enter Numbers: 1 2 3 4 5
	Top element: 5
	Popped: 5
	Top element: 4 %%
}
```