| Symbol   | Action                                 |
| -------- | -------------------------------------- |
| Operand  | print                                  |
| (        | push                                   |
| )        | pop till (                             |
| Operator | pop stronger/equal operators then push |
| End      | pop all                                |
```c

#include<stdio.h>
#include<ctype.h>
char stack[100];
int top=-1;
char pop(){
    return stack[top--];
}
void push(char x){
    stack[++top]=x;
}
int precedence(char x){
        if(x=='+' || x=='-'){
            return 1;
        }
        if(x=='*'||x=='/'){
            return 2;
        }
        if(x=='^'){
            return 3;
        }
        return 0;
}
int main(){
    char infix[100];
    printf("Enter the infix expression");
    scanf("%s",infix);
    for(int i=0;infix[i]!='\0';i++){
        char ch=infix[i];
        if(isalnum(ch)){
            printf("%c",ch);
        }
        else if(ch=='('){
            push(ch);
        }
        else if(ch==')'){
            while(top!=-1 && stack[top]!='('){
                printf("%c",pop());
            }
            pop();
        }
        else{
            while(top!=-1 && precedence(stack[top])>=precedence(ch)){
                printf("%c",pop());
            }
            push(ch);
        }
    }
    while(top!=-1){
        printf("%c",pop());
    }
}
```
