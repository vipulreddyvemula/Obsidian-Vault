==**Declaration**==
```cpp
#include<iostream>
#include<string>
array<int,3>arr;       // -> {0,0,0}
int main(){
	array<int,5> arr;      // -> declaration
	
	arr.fill(10);          // {10,10,10,10,10}  -> fills 10 in all places
	
	arr.at(index);         // -> to acces an element in array
	
	
	
}
```
==**Iterators**==
### C++ String Iterator Functions

- `begin()`     :- Points to the start of the string (first character).

- `end()`          :- Points past the last character of the string (one-past-the-end).

- `rbegin()`   :-  Points to the last character of the string (reverse begin).

- `rend()`        :-   Points before the first character of the string (reverse end).

- `cbegin()`   :-   Const iterator to the start of the string (read-only).

- `cend()`        :-   Const iterator to the end of the string (read-only).


```cpp
array<int, 5> arr = {1, 3, 4, 5, 6}; 

// Forward iteration using iterators from begin() to end()
for(auto it : arr.begin(); it != arr.end(); it++) {
    cout << *it << " ";  // Dereference iterator to get value
}


// Reverse iteration using reverse iterators from rbegin() to rend()
for(auto it : arr.rbegin(); it != arr.rend(); it++) {
    cout << *it << " ";  // Dereference iterator for reverse order
}


// Reverse iteration using normal iterators by decrementing
for(auto it : arr.end() - 1; it >= arr.begin(); it--) {
    cout << *it << " ";  // Dereference iterator to get value
}


// Range-based for loop (simpler and more readable)
for(auto it : arr) {
    cout << it << " ";    // Directly get value from array element
}




string s = "xhegcwe"; 

// Range-based for loop over string characters
for(auto c : s) {
    cout << c << " ";  // Prints each character in string
}




// Array size
cout << arr.size();    // Number of elements in the array

// First element (equivalent to arr.at(0))
cout << arr.front();   

// Last element (equivalent to arr.at(arr.size() - 1))
cout << arr.back();    

```



