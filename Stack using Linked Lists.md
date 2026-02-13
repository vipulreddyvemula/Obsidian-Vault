```cpp
#include <stdio.h>
#include <stdlib.h>

/* Structure for each stack node */
struct node {
    int data;          // value stored in stack node
    struct node *next; // pointer to next node (below it in stack)
};


/* PUSH FUNCTION
   top = address of stack pointer
   value = number to insert */
void push(struct node **top, int value) {

    // create a new node in heap memory
    struct node *newNode = (struct node *)malloc(sizeof(struct node));

    // if memory allocation fails
    if (newNode == NULL) {
        printf("Heap Overflow\n");
        return;
    }

    // store value inside node
    newNode->data = value;

    // make new node point to current top node
    // (*top is the actual stack pointer like stack1)
    newNode->next = *top;

    // move stack top to new node
    // so new node becomes first element
    *top = newNode;
}


/* POP FUNCTION
   removes top element from stack */
int pop(struct node **top) {

    // if stack is empty
    if (*top == NULL) {
        printf("Stack Underflow\n");
        return -1;
    }

    // store current top node
    struct node *temp = *top;

    // save its value
    int poppedValue = temp->data;

    // move top pointer to next node
    // so second element becomes new top
    *top = temp->next;

    // delete old top node from memory
    free(temp);

    // return removed value
    return poppedValue;
}


/* PEEK FUNCTION
   shows value of top element */
void peek(struct node *top) {

    // if stack empty
    if (top == NULL) {
        printf("Stack is empty\n");
    } 
    else {
        // print data stored in top node
        printf("Top element: %d\n", top->data);
    }
}


/* TRAVERSE FUNCTION
   prints entire stack from top to bottom */
void traverse(struct node *top) {

    // if empty
    if (top == NULL) {
        printf("Stack is empty\n");
        return;
    }

    // loop through all nodes
    while (top != NULL) {
        printf("%d ", top->data); // print value
        top = top->next;          // move to next node
    }

    printf("\n");
}


int main() {

    // two stacks initially empty
    struct node *stack1 = NULL;
    struct node *stack2 = NULL;

    // push elements into stack1
    push(&stack1, 10);
    push(&stack1, 20);
    push(&stack1, 30);
    push(&stack1, 40);

    /* Transfer all elements from stack1 to stack2
       This reverses order */
    while (stack1 != NULL) {

        // remove top element from stack1
        int value = pop(&stack1);

        // push that element into stack2
        push(&stack2, value);
    }

    // print second stack
    printf("Second Stack:\n");

    peek(stack2);      // show top value
    traverse(stack2);  // print all values

    return 0;
}

```