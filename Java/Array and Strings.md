Daksh, in Java **arrays do not have many “functions” like strings**. Arrays mainly use **`length` property** and common operations using loops. Strings have many built-in methods like `length()`, `charAt()`, `concat()`, `substring()`, etc. Your array notes cover declaration, creation, initialization, `length`, indexing, copying, passing/returning arrays, and 2D arrays; your string notes list many string operations and methods.

# 1. Array Short Notes

## Array declaration

```java
int[] a;
double[] marks;
String[] names;
```

Meaning: creates only a reference variable, not actual array.

## Array creation

```java
int[] a = new int[5];
```

Meaning: creates an integer array of size `5`.

Valid indexes:

```java
a[0], a[1], a[2], a[3], a[4]
```

Invalid:

```java
a[5]; // ArrayIndexOutOfBoundsException
```

Index starts from `0` and ends at `n - 1`.

## Array initialization

```java
int[] a = {10, 20, 30, 40};
```

This means:

```java
a[0] = 10;
a[1] = 20;
a[2] = 30;
a[3] = 40;
```

## Default values in array

|Array type|Default value|
|---|---|
|`int`, `long`, `double`|`0`, `0.0`|
|`boolean`|`false`|
|`char`|`'\u0000'`|
|Object/String|`null`|

## `length`

```java
int[] a = {10, 20, 30};
System.out.println(a.length);
```

Output:

```text
3
```

Important: array uses **`length`**, not `length()`.

```java
a.length;   // correct
a.length(); // wrong
```

## Accessing array elements

```java
int[] a = {10, 20, 30};
System.out.println(a[0]); // 10
System.out.println(a[2]); // 30
```

## Updating array element

```java
int[] a = {10, 20, 30};
a[1] = 99;
System.out.println(a[1]);
```

Output:

```text
99
```

## Printing array using loop

```java
int[] a = {10, 20, 30};

for (int i = 0; i < a.length; i++) {
    System.out.println(a[i]);
}
```

## Printing array using enhanced for loop

```java
int[] a = {10, 20, 30};

for (int x : a) {
    System.out.println(x);
}
```

## Sum of array elements

```java
int[] a = {10, 20, 30};
int sum = 0;

for (int x : a) {
    sum += x;
}

System.out.println(sum);
```

Output:

```text
60
```

## Largest element

```java
int[] a = {10, 50, 20};
int max = a[0];

for (int i = 1; i < a.length; i++) {
    if (a[i] > max) {
        max = a[i];
    }
}

System.out.println(max);
```

Output:

```text
50
```

## Copying array: wrong way

```java
int[] a = {1, 2, 3};
int[] b = a;
```

This does **not** create a new copy. Both `a` and `b` refer to the same array.

## Copying array: correct way

```java
int[] a = {1, 2, 3};
int[] b = new int[a.length];

for (int i = 0; i < a.length; i++) {
    b[i] = a[i];
}
```

Your notes specifically warn that assignment copies reference, while loop copying copies actual elements.

## Passing array to method

```java
static void printArray(int[] a) {
    for (int x : a) {
        System.out.print(x + " ");
    }
}

public static void main(String[] args) {
    int[] list = {3, 1, 2, 6};
    printArray(list);
}
```

## Returning array from method

```java
static int[] reverse(int[] a) {
    int[] result = new int[a.length];

    for (int i = 0, j = a.length - 1; i < a.length; i++, j--) {
        result[j] = a[i];
    }

    return result;
}
```

Your notes include both passing arrays to methods and returning arrays from methods.

## 2D array

```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6}
};
```

Access:

```java
System.out.println(matrix[0][1]);
```

Output:

```text
2
```

## Printing 2D array

```java
int[][] a = {
    {1, 2, 3},
    {4, 5, 6}
};

for (int row = 0; row < a.length; row++) {
    for (int col = 0; col < a[row].length; col++) {
        System.out.print(a[row][col] + " ");
    }
    System.out.println();
}
```

## Jagged array

```java
int[][] a = {
    {1, 2, 3},
    {4, 5},
    {6}
};
```

Rows can have different lengths.

# 2. String Short Notes

A `String` is a sequence of characters. In Java, strings are objects of the `String` class. Strings are **immutable**, meaning their contents cannot be changed after creation. Your notes also mention that string literals are stored in the **string constant pool**.

```java
String s1 = "Java";
String s2 = new String("Java");
```

## Important string methods

|Method|Meaning|Example|
|---|---|---|
|`length()`|Returns number of characters|`"Java".length()` → `4`|
|`charAt(i)`|Returns character at index `i`|`"Java".charAt(0)` → `'J'`|
|`concat(str)`|Joins two strings|`"Core".concat("Java")`|
|`equals(str)`|Compares content|`"Java".equals("Java")` → `true`|
|`equalsIgnoreCase(str)`|Compares content ignoring case|`"java".equalsIgnoreCase("JAVA")` → `true`|
|`compareTo(str)`|Lexicographic comparison|`"apple".compareTo("banana")` → negative|
|`substring(begin)`|Returns substring from begin index|`"Sachin".substring(2)` → `"chin"`|
|`substring(begin, end)`|Begin inclusive, end exclusive|`"Sachin".substring(0, 3)` → `"Sac"`|
|`contains(str)`|Checks whether string contains given sequence|`"Java".contains("av")` → `true`|
|`isEmpty()`|Checks if string length is 0|`"".isEmpty()` → `true`|
|`indexOf(ch)`|Returns first index of character|`"Java".indexOf('a')` → `1`|
|`indexOf(str)`|Returns first index of substring|`"Java Program".indexOf("Pro")` → `5`|
|`lastIndexOf(ch)`|Returns last index of character|`"Java".lastIndexOf('a')` → `3`|
|`replace(old, new)`|Replaces characters/strings|`"Java".replace('a','o')` → `"Jovo"`|
|`split(regex)`|Splits string into array|`"a,b,c".split(",")`|
|`toUpperCase()`|Converts to uppercase|`"java".toUpperCase()` → `"JAVA"`|
|`toLowerCase()`|Converts to lowercase|`"JAVA".toLowerCase()` → `"java"`|
|`trim()`|Removes beginning and ending spaces|`" Java ".trim()` → `"Java"`|
|`valueOf(value)`|Converts value to string|`String.valueOf(10)` → `"10"`|
|`intern()`|Returns pooled string reference|`s.intern()`|
|`format()`|Returns formatted string|`String.format("%d", 10)`|
|`join()`|Joins strings using delimiter|`String.join("-", "A", "B")` → `"A-B"`|

Your string notes list methods like `charAt`, `length`, `format`, `substring`, `contains`, `join`, `equals`, `isEmpty`, `concat`, `replace`, `equalsIgnoreCase`, `split`, `intern`, `indexOf`, `toLowerCase`, `toUpperCase`, `trim`, and `valueOf`.

# 3. String Method Examples

## `length()`

```java
String s = "Welcome";
System.out.println(s.length());
```

Output:

```text
7
```

## `charAt()`

```java
String s = "Window";
System.out.println(s.charAt(2));
```

Output:

```text
n
```

String indexing starts from `0`, just like arrays.

## `concat()` and `+`

```java
String a = "Core";
String b = "Java";

System.out.println(a + b);
System.out.println(a.concat(b));
```

Output:

```text
CoreJava
CoreJava
```

Your notes say strings can be concatenated using `+` or `concat()`.

## `equals()` vs `==`

```java
String s1 = "Sachin";
String s2 = "Sachin";
String s3 = new String("Sachin");

System.out.println(s1.equals(s3));
System.out.println(s1 == s3);
```

Output:

```text
true
false
```

`equals()` compares content.  
`==` compares reference/address. Your notes clearly say `==` checks whether two references point to the same instance.

## `equalsIgnoreCase()`

```java
String s1 = "Sachin";
String s2 = "SACHIN";

System.out.println(s1.equalsIgnoreCase(s2));
```

Output:

```text
true
```

## `compareTo()`

```java
String a = "apple";
String b = "berry";

System.out.println(a.compareTo(b));
```

Output: negative value, because `"apple"` comes before `"berry"`.

Rules:

```text
s1.compareTo(s2) = 0        means equal
s1.compareTo(s2) > 0        means s1 greater
s1.compareTo(s2) < 0        means s1 smaller
```

Your notes mention that `compareTo()` returns `0`, positive, or negative depending on comparison.

## `substring()`

```java
String s = "Sachin Tendulkar";

System.out.println(s.substring(6));
System.out.println(s.substring(0, 6));
```

Output:

```text
Tendulkar
Sachin
```

Important:

```text
startIndex = included
endIndex = excluded
```

## `contains()`

```java
String s = "Java Programming";
System.out.println(s.contains("Program"));
```

Output:

```text
true
```

## `indexOf()`

```java
String s = "Java Programming";

System.out.println(s.indexOf('a'));
System.out.println(s.indexOf("Program"));
```

Output:

```text
1
5
```

## `replace()`

```java
String s = "Java";
System.out.println(s.replace('a', 'o'));
```

Output:

```text
Jovo
```

## `split()`

```java
String s = "red,green,blue";
String[] colors = s.split(",");

for (String c : colors) {
    System.out.println(c);
}
```

Output:

```text
red
green
blue
```

## `toUpperCase()` and `toLowerCase()`

```java
String s = "Java";

System.out.println(s.toUpperCase());
System.out.println(s.toLowerCase());
```

Output:

```text
JAVA
java
```

## `trim()`

```java
String s = "   Java   ";
System.out.println(s.trim());
```

Output:

```text
Java
```

## `valueOf()`

```java
int x = 100;
String s = String.valueOf(x);

System.out.println(s + 20);
```

Output:

```text
10020
```

# 4. StringBuffer Short Notes

`String` is immutable, but `StringBuffer` is mutable. It can be changed using append, insert, replace, and delete. Your notes say `StringBuffer` represents growable and writable character sequences and can automatically grow when needed.

## Constructors

```java
StringBuffer sb1 = new StringBuffer();
StringBuffer sb2 = new StringBuffer(50);
StringBuffer sb3 = new StringBuffer("Java");
```

## Important StringBuffer methods

|Method|Meaning|Example|
|---|---|---|
|`append()`|Adds at end|`sb.append(" World")`|
|`insert()`|Inserts at index|`sb.insert(0, "Core ")`|
|`replace()`|Replaces part|`sb.replace(0, 4, "Python")`|
|`delete()`|Deletes part|`sb.delete(0, 2)`|
|`reverse()`|Reverses string|`sb.reverse()`|
|`length()`|Returns length|`sb.length()`|
|`capacity()`|Returns buffer capacity|`sb.capacity()`|

Example:

```java
StringBuffer sb = new StringBuffer("Java");

sb.append(" Programming");
System.out.println(sb);

sb.insert(5, "Core ");
System.out.println(sb);

sb.replace(0, 4, "Python");
System.out.println(sb);

sb.delete(0, 7);
System.out.println(sb);
```

# 5. Last-Minute Must Remember

| Topic             | Must remember                 |
| ----------------- | ----------------------------- |
| Array length      | `arr.length`, no brackets     |
| String length     | `str.length()`, with brackets |
| Array index       | Starts at `0`                 |
| String index      | Starts at `0`                 |
| Array copy        | Use loop, not direct `=`      |
| String comparison | Use `.equals()`, not `==`     |
| String            | Immutable                     |
| StringBuffer      | Mutable                       |
| substring         | Start included, end excluded  |
| charAt            | Gives character at index      |
| split             | Returns `String[]` array      |