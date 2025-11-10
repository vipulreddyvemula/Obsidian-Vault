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

---

### clear()

vec.clear(); // --> erase all elements at once {}
```

==**Copying vectors**==
```cpp
	vector<int> vec1(4, 0); // -> {0,0,0,0}
	vector<int> vec2(4, 10); // -> {10,10,10,10}
 
	// copy the entire vec2 into vec3
	vector<int> vec3(vec2.begin(), vec2.end()); // -> [)
	vector<int> vec3(vec2); 
```

==**Using  pointer**==
```cpp
	// begin(), end(), rbegin(), rend() --> these act like pointers
	vector<int> raj;
	raj.push_back(1); // raj.emplace_back(1); // emplace_back takes lesser time than push back 
	raj.push_back(3); 
	raj.push_back(2); 
	raj.push_back(5); // -> {1, 3, 2, 5} 
 
	vector<int> raj1(raj.begin(), raj.begin() + 2);  // -> {1, 3}  
```

==**Defining 2D vector**==
```cpp
	vector<vector<int>> vec; 
 
	vector<int> raj1;
	raj1.push_back(1); 
	raj1.push_back(2); 
 
	vector<int> raj2;
	raj2.push_back(10); 
	raj2.push_back(20); 
 
	vector<int> raj3;
	raj3.push_back(19); 
	raj3.push_back(24); 
	raj3.push_back(27); 
 
	vec.push_back(raj1); 
	vec.push_back(raj2); 
	vec.push_back(raj3); 
```

2D vector for loop
```cpp
	for(auto vctr: vec) {
		for(auto it: vctr) {
			cout << it << " "; 
		}
		cout << endl; 
	}
 
 
	for(int i = 0;i<vec.size();i++) {
		for(int j = 0;j<vec[i].size();j++) {
			cout <<  vec[i][j] << " "; 
		}
		cout << endl; 
	}
```

==**Defining 10x20 vector**==
```cpp
	// define 10 x 20 
	vector<vector<int>> vec(10, vector<int> (20, 0)); 
	vec.push_back(vector<int>(20, 0)); 
	cout << vec.size() << endl; // 11 prints
	
    //Accesses the 3rd row (vec[2]) and adds a new element 1 at the end.
	vec[2].push_back(1); 
	
	//arr is an array of 4 vectors of integers.
	vector<int> arr[4]; 
	arr[1].push_back(0);
	//Accesses the 2nd vector (`arr[1]`) and pushes back `0` into it, adding one element `0` to that vector.


```


==**Defining 3D vectors**==
```cpp
	// 10 x 20 x 30 // int arr[10][20][30] 
	vector<vector<vector<int>>> vec(10, vector<vector<int>> vec(20, vector<int> (30, 0));)
```
