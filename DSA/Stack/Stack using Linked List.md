Related: [[Linked Lists]]

==Simple code without comments and notes for== 
==Create two stacks implemented by linked list. Pop all the elements from one stack and==
==push them into another one. Then peek/traverse all the elements in 2nd stack==
```cpp
#include<stdio.h>
#include<stdlib.h>
struct node{
    int data;
    struct node* next;
};
void push(struct node** top,int value){
    struct node* newnode=(struct node*)malloc(sizeof(struct node));
    if(newnode==NULL){
        printf("Heap Overflow");
        return;
    }
    newnode->data=value;
    newnode->next=*top;
    *top=newnode;
}
int pop(struct node** top){
    if(*top==NULL){
        printf("Stack underflow");
        return -1;
    }
    struct node *temp=*top;
    int poppedvalue=temp->data;
    *top=temp->next;
    free(temp);
    return poppedvalue;


}
void traverse(struct node* top){
    if(top==NULL){
        printf("stack is empty");
        return;
    }
    while(top!=NULL){
        printf("%d\n",top->data);
        top=top->next;
    }
    printf("\n");

}
void peek(struct node *top){
    if(top==NULL){
        printf("Stack is empty");
        return;
    }
    printf("Top element is: %d\n",top->data);
}
int main(){
    struct node *stack1=NULL;
    struct node *stack2=NULL;
    push(&stack1,10);
    push(&stack1,20);
    push(&stack1,30);
    push(&stack1,40);
    while (stack1 != NULL) {
        int value = pop(&stack1);
        push(&stack2, value);
    }
    printf("Second Stack:\n");
    peek(stack2);
    traverse(stack2);

    return 0;


}
```


Same question answer with notes to understand it
```scss
stack1        → pointer variable (top of stack)

&stack1       → address of stack pointer

top           → pointer to stack pointer

*top          → actual stack pointer

**top         → actual node (rarely used)

```


```cpp
#include<stdio.h>
#include<stdlib.h>

struct node{
    int data;
    struct node* next;
};

/*
top is NOT the stack.
top is the ADDRESS of the stack pointer.

When we call push(&stack1, value):

top = &stack1        (address of stack pointer)
*top = stack1        (actual top node pointer)

So:
top  -> points to stack1
*top -> is stack1
*/
void push(struct node** top,int value){

    struct node* newnode=(struct node*)malloc(sizeof(struct node));

    if(newnode==NULL){
        printf("Heap Overflow");
        return;
    }

    newnode->data=value;

    /*
    *top is current top node.
    So this links new node to old stack.
    */
    newnode->next=*top;

    /*
    This changes stack1 itself to point to newnode.

    NOT modifying a node.
    Modifying the stack pointer.

    stack1 = newnode
    */
    *top=newnode;
}

int pop(struct node** top){

    /*
    *top == NULL means stack1 == NULL
    → stack empty → nothing to pop
    */
    if(*top==NULL){
        printf("Stack underflow");
        return -1;
    }

    /*
    temp stores current top node
    temp and stack1 both point to same node
    */
    struct node *temp=*top;

    int poppedvalue=temp->data;

    /*
    Move stack pointer to next node

    stack1 = temp->next
    */
    *top=temp->next;

    /*
    delete old top node
    */
    free(temp);

    return poppedvalue;
}

void traverse(struct node* top){

    /*
    Here top is NOT double pointer.
    It's just a copy of stack pointer.
    Changing it will NOT affect original stack.
    */

    if(top==NULL){
        printf("stack is empty");
        return;
    }

    while(top!=NULL){
        printf("%d\n",top->data);

        /*
        move local pointer forward
        (original stack unchanged)
        */
        top=top->next;
    }

    printf("\n");
}

void peek(struct node *top){

    /*
    top here = copy of stack pointer
    */
    if(top==NULL){
        printf("Stack is empty");
        return;
    }

    printf("Top element is: %d\n",top->data);
}

int main(){

    /*
    stack1 is pointer to top node of stack
    Initially empty → NULL
    */
    struct node *stack1=NULL;
    struct node *stack2=NULL;

    /*
    &stack1 = address of stack1
    So push can modify stack1 itself
    */
    push(&stack1,10);
    push(&stack1,20);
    push(&stack1,30);
    push(&stack1,40);

    /*
    Move all elements from stack1 → stack2
    This reverses stack
    */
    while (stack1 != NULL) {
        int value = pop(&stack1);
        push(&stack2, value);
    }

    printf("Second Stack:\n");

    peek(stack2);
    traverse(stack2);

    return 0;
}

```