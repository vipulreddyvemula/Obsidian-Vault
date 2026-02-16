Simple Implementation of Deque Using Array
```cpp
#include<stdio.h>
#define max 5
int arr[max];
int front=-1;
int rear=-1;
void insertrear(int value){
    if(rear==max-1){
        printf("deque overflow");
    }
    if(front==-1){
        front=0;
    }
    rear++;
    arr[rear]=value;
}
void deletefront(){
    if(front>rear || front==-1 ){
        printf("Deque UNderflow\n");
    }

    printf("Deleted from front: %d\n", arr[front]);
    front++;
}
void insertfront(int value){
    if(front==0){
        printf("No space at front\n");
    }
    if(front==-1){
        front=rear=0;
        arr[front]=value;
        return;
    }
    front--;
    arr[front]=value;

}
void deleterear(){
    if(front=-1 || front>rear){
        printf("Deque Underflow\n");
    }
    printf("Deleted from rear: %d\n", arr[rear]);
    rear--;
}
int main(){
    insertRear(10);
    insertRear(20);
    insertRear(30);

    display();

    insertFront(5);
    display();

    deleteRear();
    display();

    deleteFront();
    display();
}
```