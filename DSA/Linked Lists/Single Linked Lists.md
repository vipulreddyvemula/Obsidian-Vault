```cpp
/* SINGLY LINKED LIST */

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;              // value stored
    struct Node* next;     // next node address
};

/* head initialization (mandatory) */
struct Node* head = NULL;

/* =====================================================
   SINGLE POINTER STYLE (return updated head)
   ===================================================== */

/* insert at beginning */
struct Node* insertAtBeginning(struct Node* head, int value) {
    struct Node* newNode = malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = head;          // link old head
    return newNode;                // new head
}

/* insert at end */
struct Node* insertAtEnd(struct Node* head, int value) {
    struct Node* newNode = malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = NULL;

    if (head == NULL)
        return newNode;

    struct Node* temp = head;
    while (temp->next != NULL)
        temp = temp->next;

    temp->next = newNode;
    return head;
}

/* delete at beginning */
struct Node* deleteAtBeginning(struct Node* head) {
    if (head == NULL)
        return NULL;

    struct Node* temp = head;
    head = head->next;
    free(temp);
    return head;
}

/* delete by value */
struct Node* deleteByValue(struct Node* head, int key) {
    struct Node* temp = head;
    struct Node* prev = NULL;

    if (temp != NULL && temp->data == key) {
        head = temp->next;
        free(temp);
        return head;
    }

    while (temp != NULL && temp->data != key) {
        prev = temp;
        temp = temp->next;
    }

    if (temp == NULL)
        return head;

    prev->next = temp->next;
    free(temp);
    return head;
}

/* traversal */
void printList(struct Node* head) {
    struct Node* temp = head;
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}
```


**==DOUBLE POINTER STYLE (modify head directly)==**

```cpp

/* =====================================================
   DOUBLE POINTER STYLE (modify head directly)
   ===================================================== */

/* insert at beginning */
void insertAtBeginningDP(struct Node** head, int value) {
    struct Node* newNode = malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = *head;     // old head
    *head = newNode;           // update head
}

/* insert at end */
void insertAtEndDP(struct Node** head, int value) {
    struct Node* newNode = malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = NULL;

    if (*head == NULL) {
        *head = newNode;
        return;
    }

    struct Node* temp = *head;
    while (temp->next != NULL)
        temp = temp->next;

    temp->next = newNode;
}

/* delete at beginning */
void deleteAtBeginningDP(struct Node** head) {
    if (*head == NULL)
        return;

    struct Node* temp = *head;
    *head = (*head)->next;
    free(temp);
}

/* delete by value */
void deleteByValueDP(struct Node** head, int key) {
    struct Node* temp = *head;
    struct Node* prev = NULL;

    if (temp != NULL && temp->data == key) {
        *head = temp->next;
        free(temp);
        return;
    }

    while (temp != NULL && temp->data != key) {
        prev = temp;
        temp = temp->next;
    }

    if (temp == NULL)
        return;

    prev->next = temp->next;
    free(temp);
}
```


**==MAIN FUNCTION FOR BOTH SINGLE AND DOUBLE POINTERS==**
```cpp
int main() {

    /* using single pointer style */
    head = insertAtBeginning(head, 10);
    head = insertAtBeginning(head, 20);
    head = insertAtEnd(head, 30);
    printList(head);              // 20 -> 10 -> 30 -> NULL

    head = deleteAtBeginning(head);
    printList(head);              // 10 -> 30 -> NULL

    /* using double pointer style */
    insertAtBeginningDP(&head, 40);
    insertAtEndDP(&head, 50);
    printList(head);              // 40 -> 10 -> 30 -> 50 -> NULL

    deleteByValueDP(&head, 10);
    printList(head);              // 40 -> 30 -> 50 -> NULL

    return 0;
}

```



==**MY CODE**== FOR (Write a program to create a singly linked list of five integer data, then multiply each data by 5 and print the elements of the linked list)

```cpp
#include<stdio.h>
#include<stdlib.h>
struct node{
    int data;
    struct node *next;
};
int main(){
    int n;
    scanf("%d",&n);
    struct node *new,*temp;
    int data;
    new=(struct node*)malloc(sizeof(struct node));
    printf("enter the data of 1: ");
    scanf("%d",&data);
    new->data=data;
    new->next=NULL;
    struct node* header=new;
    temp=new;
    for(int i=2;i<=n;i++){
        new = (struct node*)malloc(sizeof(struct node));
        printf("enter the data of %d: ",i);
        scanf("%d",&data);
        new->data=data;   //(*new).data=data
        new->next=NULL;   //(*new).next=NULL;
        temp->next=new;   //(*temp).next=new;
        temp=temp->next;  //temp=(*temp).next;



    }
    struct node* temp1=header;
    int x;
    printf("Enter the  number with which you want to multiply: ");
    scanf("%d",&x);
    while(temp1!=NULL){
        printf("%d\n",(temp1->data)*x);
        temp1=temp1->next;

    }

}
```