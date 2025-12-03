## File I/O in C – Quick Notes

## 1. Header
```c
#include <stdio.h>
```

## 2. Opening a file – fopen

```c
FILE *fp;
 fp = fopen("filename.txt", "r");   // open for reading 
 fp = fopen("filename.txt", "w");   // open for writing (truncate/create) 
 fp = fopen("filename.txt", "a");   // open for appending 
 fp = fopen("data.bin", "rb");      // binary read 
 fp = fopen("data.bin", "wb");      // binary write
```
Always check:
```c
if (fp == NULL) { 
    // handle error 
}
```
## 3. Closing a file – fclose
```c
fclose(fp);
```
## 4. Character I/O – fgetc, fputc
```c
int ch = fgetc(fp);          // read one char 
fputc('A', fp);              // write one char
```
## 5. Line I/O – fgets, fputs
```c
char buf[100]; 
fgets(buf, sizeof(buf), fp); // read one line (including '\n' if present)
fputs("Hello\n", fp);        // write a string (no automatic '\n')
```
## 6. Formatted I/O – fprintf, fscanf

```c
fprintf(fp, "Value = %d\n", x);          // write formatted data 
fscanf(fp, "%d %f", &a, &b);             // read formatted data
```
## 7. Binary I/O – fread, fwrite
```c
int arr[10]; // write 10 ints 
fwrite(arr, sizeof(int), 10, fp); // read 10 ints 
fread(arr, sizeof(int), 10, fp);
```
## 8. Typical pattern (read file)
```c
FILE *fp = fopen("input.txt", "r");
if (fp == NULL) {
    printf("Cannot open file\n");
    return 1;
}

int x;
while (fscanf(fp, "%d", &x) == 1) {
    // use x
}

fclose(fp);
```
