==To Print Full Name Using Strings==
```c
#include<stdio.h>
char name[15];
int main() {
    gets(name);
    puts(name);
  
  
    fgets(name, 15, stdin);
    puts(name);

    return 0;

}
```
**==strings==**
```c
# include <stdio.h>
# include <string.h>

int main() {
    //declaration
    char name[] = "Shradha Khapra";
    
    //printing string
    for(int i=0; name[i] != '\0'; i++) {
        printf("%c", name[i]);
    }
    printf("\n");
    
    //printing string with pointer
    for(char *ptr=name; *ptr != '\0'; ptr++) {
        printf("%c", *ptr);
    }
    printf("\n");
    //printing using format specifier
    printf("%s\n", name);
    
    
    //input a string
    char firstName[40];
    printf("enter first name : ");
    scanf("%s", firstName);
    printf("you first name is %s\n", firstName);
    char fullName[40];
    printf("enter full name : ");
    scanf("%s", fullName);
    printf("you first name is %s\n", fullName);
    // gets & puts
    char fullName[40];
    printf("enter full name : ");
    fgets(fullName, 40, stdin);
    puts(fullName);


    //Library Functions
    char name[] = "Shradha";
    int length = strlen(name);   //count number of characters excluding '\0'
    printf("the length of name : %d\n", length);
    
    
    char oldVal[] = "oldValue";
    char newVal[50];
    strcpy(newVal, oldVal);      //copies value of old string to new string
    puts(newVal);
    
    char str[100];
    fgets(str,sizeof(str),stdin);
    str[strcspn(str,"\n")]='\0';   //counts at whic h value an element(\n) is 
    
    
    char firstStr[50] = "Hello ";
    char secStr[] = "World";
    strcat(firstStr, secStr);  //concatenates first string with second string
    puts(firstStr);            //note:-first string should be large enough
    
    
    char str1[] = "Apple";      //Compares 2 strings & returns a value
    char str2[] = "Banana";               //0 -> string equal
    printf("%d\n", strcmp(str1, str2));   //positive -> first > second
                                          //negative -> first < second



    //enter String using %c

    printf("enter string : ");
    char str[100];
    char ch;
    int i = 0;
    while(ch != '\n') {
    scanf("%c", &ch);
    str[i] = ch;
    i++;
    }
    str[i] = '\0';
    puts(str);
    return 0;
}
```
