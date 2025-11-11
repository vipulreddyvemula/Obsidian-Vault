A set in [STL](https://takeuforward.org/c/c-stl-tutorial-most-frequent-used-stl-containers/ "STL") is a container that stores unique elements in a particular order.
```cpp
//commands are similar to previous stl so repeated notes is not written

set<int> st;                         //syntax
set<object_type> variable_name;      //syntax

unordered_set<int>st;                //sytnax --> unsorted unique element

multiset<int> ms;        //stores repeated values also but sorted
ms.insert(1);
ms.insert(1);
ms.insert(2);
ms.insert(3);  // -> {1,1,2,3}

ms.erase(2)  //->all instances will be erased 
ms.count(1)  //->counts number of 1 in set


include <unordered_set>    //header
include <set>



TIME COMPLEXITY:-
ORDERED SET:-  O(log n);
UNORDERED SET:- O(1) worst case(linear in nature):- O(set size);


```

==**Functions in set**==
```cpp
- **insert()** – to insert an element in the set.  

set<int> s;
s.insert(1);
s.insert(2);

- **begin()** – return an iterator pointing to the first element in the set.  
s.begin();

- **end()** – returns an iterator to the theoretical element after the last element.  
s.end();

- **count()** – returns true or false based on whether the element is present in the set or not.  
    
set<int> s;
s.insert(1);
s.insert(2);
s.count(2); //returns true


- **clear()** – deletes all the elements in the set.  
s.clear();

- **find()** – to search an element in the set.  
    
set<int> s;
s.insert(1);
s.insert(2);
if(s.find(2)!=s.end())
cout<<"true"<<endl;


- **erase()** – to delete a single element or elements between a particular range. 
s.erase();

- **size()** – returns the size of the set.  
s.size();

- **empty()** – to check if the set is empty or not.  
s.empty();
```

Youtube video example code
```cpp
//st -> {1,2,5}
//erase function

st.erase(st.begin());    // st.erase(iterator) // set -> {2,5}
st.erase(st.begin(),st.begin()+2);  // it acts like [)    -> {5}


auto it = st.find(5);  // it will be  iterator to 5
```


website example code
```cpp
```cpp
#include<bits/stdc++.h>

using namespace std;

int main() {
  set < int > s;
  for (int i = 1; i <= 10; i++) {
    s.insert(i);
  }

  cout << "Elements present in the set: ";
  for (auto it = s.begin(); it != s.end(); it++) {
    cout << * it << " ";  //Elements present in the set: 1 2 3 4 5 6 7 8 9 10
  }
  cout << endl;
  int n = 2;
  if (s.find(2) != s.end())
    cout << n << " is present in set" << endl;  //2 is present in set

  s.erase(s.begin());
  cout << "Elements after deleting the first element: ";
  for (auto it = s.begin(); it != s.end(); it++) {
    cout << * it << " "; //Elements after deleting the first element: 2 3 4                                                                 5 6 7 8 9 10
  }
  cout << endl;

  cout << "The size of the set is: " << s.size() << endl;
                                 //The size of the set is: 9
  if (s.empty() == false)
    cout << "The set is not empty " << endl;
  else
    cout << "The set is empty" << endl;
                                //The set is not empty
  s.clear();
  cout << "Size of the set after clearing all the elements: " << s.size();
                                //The size of the set is: 9
}
```
```