**==Basic implementation of queue using Array Structure==**
```cpp
#include<stdio.h>
#include<stdlib.h>
#define max 5
struct queue{
    int arr[max];
    int front;
    int rear;   
};
void create(struct queue* q){
    q->front=-1;
    q->rear=-1;

}
void enqueue(struct queue *q,int value){
    if(q->rear==max-1){
        printf("Queue overflow");
        return;
    }
    if(q->front==-1){
        q->front++;
    }
    q->rear++;
    q->arr[q->rear]=value;
    
}
void dequeue(struct queue *q){
    if(q->front==-1 || q->front>q->rear){
        printf("Queue Underflow");
        return;
    }
    printf("The deleted element is %d \n",q->arr[q->front]);
    q->front++;
}
void display(struct queue *q){
    if(q->front==-1 || q->front>q->rear){
        printf("Queue is empty");
        return;
    }
    for(int i=q->front;i<=q->rear;i++){
        printf("The element in the queue are %d  \n",q->arr[i]);;

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