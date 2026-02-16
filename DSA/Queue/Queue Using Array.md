==**Basic implementation of queue using pure array**==
```cpp
#include<stdio.h>
#define max 5
int arr[max];
int front=-1;
int rear=-1;
void enqueue(int value){
    if(rear==max-1){
        printf("Queue Overflow: ");
        return;
    }
    if(front==-1){
        front++;

    }
    rear++;
    arr[rear]=value;
    

}
void dequeue(){
    if(front==-1 || front>rear){
        printf("Queue Underflow ");
        return;
    }
    printf("The deleted element is %d\n",arr[front]);
    front++;
    
}
void display(){
    if(front==-1 || front>rear){
        printf("Queue Empty");
        return;
    }
    for(int i=front;i<=rear;i++){
        printf("The element in the Queue is %d\n",arr[i]);
    }
    printf("\n");
}
int main(){
    enqueue(10);
    enqueue(20);
    enqueue(30);
    display();

    dequeue();
    display();
    
}
```