Wrote another program to pop two elements from the stack, and push them into another
new stack. Then peek/traverse all elements in 1st and 2nd stack
```cpp
#include<stdio.h>
#include<stdlib.h>
#define max 5
struct array{
    int arr[max];
    int top;
};
typedef struct array stack;
stack *s1;
stack *s2;
void push(stack *s,int x){
    if(s->top==max-1){
        printf("Stack Overflow");
        return;
    }
    else{
        s->arr[++(s->top)]=x;
    }
}
int pop(stack *s){
    if(s->top==-1){
        printf("Stack Underflow");
        return -1;
    }
    else{
        return s->arr[(s->top)--];  
    }
}
int peek(stack *s){
    if(s->top==-1){
        printf("Stack is empty");
        return -1;
    }
    else{
        return s->arr[s->top];
    }
}
int main(){
    s1 = (stack *)malloc(sizeof(stack));
    s2 = (stack *)malloc(sizeof(stack));
    s1->top=-1;
    s2->top=-1;


    printf("Enter the numbers: ");
    for(int i=0;i<max;i++){
        int n;
        scanf("%d",&n);
        push(s1,n);
    }
    for(int i=0;i<2;i++){
        int temp=pop(s1);
        push(s2,temp);
    }
    printf("wait we will display the stacks: \n");
    for(int i=s1->top;i>-1;i--){
        printf("displaying 1 stack: %d\n",s1->arr[i]);
    }
    for(int i=s2->top;i>-1;i--){
        printf("displaying 2 stack: %d\n",s2->arr[i]);
    }
    
  %%OUTPUT:-
    Enter the numbers: 1 2 3 4 5
	wait we will display the stacks: 
	displaying 1 stack: 3
	displaying 1 stack: 2
	displaying 1 stack: 1
	displaying 2 stack: 4
	displaying 2 stack: 5 %%
}
```