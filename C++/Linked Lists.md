```cpp
#include<stdio.h>
#include<stdlib.h>
struct node{
    int data;
    struct node* next;
};
int main(){
    int n,data;
    printf("enter the number of numbers you will enter: ");
    scanf("%d",&n);
    struct node *new=(struct node*)malloc(sizeof(struct node));
    struct node *temp,*header;
    printf("enter the number 1 : ");
    scanf("%d",&data);
    new->data=data;
    new->next=NULL;
    header=new;
    temp=new;
    for(int i=2;i<=n;i++){
        printf("enter the number 2 %d : ",i);
        new = (struct node*)malloc(sizeof(struct node));
        scanf("%d",&data);
        new->data=data;
        new->next=NULL;
        temp->next=new;
        temp=new;


    }
    int x;
    printf("enter the number you want to search: ");
    scanf("%d",&x);
    int count=0;
    struct node* temp1=header;
    while(temp1!=NULL){
        if(temp1->data==x){
            count++;

        }
        temp1=temp1->next;
    }
    printf("the number of times it was found is %d\n",count);

}
```