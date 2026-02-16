**==Basic Implementation of Queue using Linked Lists==**
```cpp
#include<stdio.h>
#include<stdlib.h>
struct node{
    int data;
    struct node *next;
};
struct queue{
    struct node *front;
    struct node *rear;
};
void create(struct queue *q){
    q->front=NULL;
    q->rear=NULL;
}

void enqueue(struct queue *q,int value){
    struct node *temp=(struct node*)malloc(sizeof(struct node));
    temp->data=value;
    temp->next=NULL;

    if(q->rear==NULL){
        q->front=temp;
        q->rear=temp;
        return;
    }
    //front → [10] → [20] → [30] ← rear
    //[10 | • ] → [20 | NULL]

    q->rear->next=temp;
    q->rear=temp;

}
void dequeue(struct queue *q){
    
    if(q->front==NULL){
        printf("Queue Underflow\n");
        return;
    }
    struct node *temp=q->front; 
    printf("Deleted data is %d\n",temp->data);
    q->front=q->front->next;
    if(q->front==NULL){
        q->rear=NULL;
    }
    free(temp);
}
void display(struct queue *q){
    struct node *temp=q->front;
    if(temp==NULL){
        printf("Queue is empty\n");
        return;
    }
    while(temp){
        printf("%d ",temp->data);
        temp=temp->next;
    }
    printf("\n");
}
int main(){
    struct queue q;
    create(&q);

    enqueue(&q,10);
    enqueue(&q,20);
    enqueue(&q,30);

    display(&q);

    dequeue(&q);
    display(&q);
}

```

QUEUE USING LINKED LIST — COMPLETE VISUAL DRY RUN DIAGRAM
```
QUEUE USING LINKED LIST — COMPLETE VISUAL DRY RUN DIAGRAM
----------------------------------------------------------

PROGRAM OPERATIONS:
enqueue(10)
enqueue(20)
enqueue(30)
display()
dequeue()
display()

----------------------------------------------------------
STEP 0 — After create(&q)

front → NULL
rear  → NULL


----------------------------------------------------------
STEP 1 — enqueue(10)

New node created:
[10 | NULL]

Queue state:

front
  ↓
[10 | NULL]
  ↑
rear


----------------------------------------------------------
STEP 2 — enqueue(20)

New node:
[20 | NULL]

Link:
rear->next = temp

Queue state:

front
  ↓
[10 | • ] → [20 | NULL]
            ↑
           rear


----------------------------------------------------------
STEP 3 — enqueue(30)

New node:
[30 | NULL]

Queue state:

front
  ↓
[10 | • ] → [20 | • ] → [30 | NULL]
                         ↑
                        rear


----------------------------------------------------------
STEP 4 — display()

Traversal pointer movement:

temp → 10 → 20 → 30 → NULL

Output:
10 20 30


----------------------------------------------------------
STEP 5 — dequeue()

Before deletion:

front
  ↓
[10] → [20] → [30]
                 ↑
                rear


Store front node:
temp → [10]


Move front forward:
front → [20]


Free deleted node [10]


Final state:

front
  ↓
[20] → [30]
        ↑
       rear


----------------------------------------------------------
STEP 6 — display()

Traversal:

temp → 20 → 30 → NULL

Output:
20 30


----------------------------------------------------------
FINAL QUEUE STATE

front → [20] → [30] ← rear


----------------------------------------------------------
GOLDEN RULES TO REMEMBER

1) enqueue → always modifies rear
2) dequeue → always modifies front
3) empty queue → front = rear = NULL
4) malloc only when creating node
5) free only when deleting node

----------------------------------------------------------
MEMORY MODEL SUMMARY

enqueue → create node → attach to rear
dequeue → remove front → free node

----------------------------------------------------------

```