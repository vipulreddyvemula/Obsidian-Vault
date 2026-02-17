
```cpp
#include<stdio.h>
#include<ctype.h>
int stack[100];
int top=-1;
int pop(){
    return stack[top--];
}
void push(char x){
    stack[++top]=x;
}
int main(){
    printf("Enter the Postfix expression: \n");
    char postfix[100];
    scanf("%s",postfix);
    for(int i=0;postfix[i]!='\0';i++){
        char ch=postfix[i];
        if(isdigit(ch)){
            push(ch-'0');
        }
        else{
            int b=pop();
            int a=pop();
            switch(ch){
                case '+' : {push(a+b);break;}
                case '-' : {push(a-b);break;}
                case '*' : {push(a*b);break;}
                case '/' : {push(a/b);break;}
            }
        }
    }
    printf("Result = %d", pop());

}
```