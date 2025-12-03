## Dynamic memory allocation – C syntax
- Header:
    - `#include <stdlib.h>`
## malloc
- Syntax:   
 ```c
   ptr = (type *)malloc(n * sizeof(type));
```
  
- Example:
    ```c
    int *a = (int *)malloc(10 * sizeof(int));
    ```
## calloc
- Syntax:
    ```c
    ptr = (type *)calloc(n, sizeof(type));    
    ```
- Example:
    ```c
    int *a = (int *)calloc(10, sizeof(int));
    ```
- Note: Initializes allocated bytes to 0.
## realloc
- Syntax:
    ```c
    - `ptr = (type *)realloc(old_ptr, new_n * sizeof(type));`
    ```    
- Example:
    ```c
    - `a = (int *)realloc(a, 20 * sizeof(int));`
    ```
## free
- Syntax:
```c
    - `free(ptr);`
    ```
- Example:
 ```c
    - `free(a);`
    ```    
- Note: Always `free` dynamically allocated memory when done.