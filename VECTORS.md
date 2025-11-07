==**Vector Syntax**==
```cpp
#include<iostream>
#include<vector>
using namespace std;
int main(){
    vector<int> vec;
    vector<int> vec1 = {1,2,3};
    vector<int> vec2(3,0);

    cout<<vec1[0]<<endl;
}
```


==**Vector For loop**==
```cpp
#include<iostream>
#include<vector>
using namespace std;
int main(){
    vector<int> vec = {1,2,3};
    vector<char> vec1 = {'a','b','c'};
    for(int value : vec){
        cout<<value<<endl;
    }
    for(char value : vec1){
        cout<<value<<endl;
    }
}
```


==**Vector Functions**==
```cpp
## Vector Functions (C++ STL)
### size()
// Returns number of elements in the vector
vector<int> v = {1, 2, 3};
size_t n = v.size(); // n = 3
capacity  = v.capacity();  // prints the total spaces of vector including                                empty
---

### push_back()
// Adds an element at the end
vector<int> v;
v.push_back(10); // v: [10]

---

### pop_back()
// Removes last element
vector<int> v = {1, 2, 3};
v.pop_back(); // v: [1, 2]

---

### front()
// Returns a reference to the first element
vector<int> v = {5, 6, 7};
int first = v.front(); // first = 5

---

### back()
// Returns a reference to the last element
vector<int> v = {8, 9, 10};
int last = v.back(); // last = 10

---

### at()
// Returns element at index (with bounds-check)
vector<int> v = {3, 4, 5};
int item = v.at(1); // item = 4
// v.at(10); // Throws out_of_range if index invalid

```
z