# Exception Handling Keywords

Java provides **5 keywords** for handling exceptions:

| Keyword   | Purpose                       |
| --------- | ----------------------------- |
| `try`     | Code that may cause exception |
| `catch`   | Handles exception             |
| `finally` | Executes always               |
| `throw`   | Manually throw exception      |
| `throws`  | Declare exception             |
# try–catch Block

Used to **catch and handle exceptions**.

Example:
```java
class Test{  
    public static void main(String[] args){  
        try{  
            int a = 10;  
            int b = 0;  
            int c = a/b;  
        }  
        catch(ArithmeticException e){  
            System.out.println("Cannot divide by zero");  
        }  
    }  
}
Output:-
Cannot divide by zero
```

---
# Multiple Catch Blocks

You can catch **different exceptions separately**.
```java
try{  
    int arr[] = new int[5];  
    arr[6] = 10;  
}  
catch(ArithmeticException e){  
    System.out.println("Arithmetic Error");  
}  
catch(ArrayIndexOutOfBoundsException e){  
    System.out.println("Array index error");  
}
```

---
# finally Block

The `finally` block **always executes**, whether an exception occurs or not.

Example:
```java
try{  
    int a = 5/0;  
}  
catch(ArithmeticException e){  
    System.out.println("Exception caught");  
}  
finally{  
    System.out.println("This always runs");  
}
```
Output:-
```
Exception caught  
This always runs
```

---
# throw Keyword

Used to **explicitly throw an exception**.

Example:
```java
class Test{  
    static void checkAge(int age){  
        if(age < 18){  
            throw new ArithmeticException("Not eligible");  
        }  
        else{  
            System.out.println("Eligible");  
        }  
    }  
  
    public static void main(String[] args){  
        checkAge(16);  
    }  
}
```

---
