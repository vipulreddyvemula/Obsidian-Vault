A set in [STL](https://takeuforward.org/c/c-stl-tutorial-most-frequent-used-stl-containers/ "STL") is a container that stores unique elements in a particular order.
```cpp
//commands are similar to previous stl so repeated notes is not written

set<int> st;                         //syntax
set<object_type> variable_name;      //syntax

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