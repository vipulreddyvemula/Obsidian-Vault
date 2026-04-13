```cpp
#include<stdio.h>
int main(){
    int arr[]={9,4,7,1,3,5};
    int n=6;
    for(int i=0;i<n-1;i++){
        for(int j=0;j<n-i-1;j++){
            if(arr[j]>arr[j+1]){
                int temp=arr[j+1];
                arr[j+1]=arr[j];
                arr[j]=temp;
            }
        }
    }
    for(int i=0;i<n;i++){
        printf("%d ",arr[i]);
        
    }
}
```
