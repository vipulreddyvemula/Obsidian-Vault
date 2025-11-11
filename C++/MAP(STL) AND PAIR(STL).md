```cpp
#include <map>
#include <iostream>
using namespace std;

// map only stores unique keys
// log n is the tc of map

map<string, int> mpp; // container holding pairs in sorted order by key

mpp["raj"] = 27;       // raj: 27 is inserted (sorted by key)
mpp["hima"] = 31;      // hima: 31 is inserted (sorted by key)
mpp["praveer"] = 31;   // praveer: 31 is inserted (sorted by key)
mpp["sandeep"] = 67;   // sandeep: 67 is inserted (sorted by key)
/*
The map holds:
-------------------------------
| hima     | 31               |
| praveer  | 31               |
| raj      | 27               |
| sandeep  | 67               |
-------------------------------
Keys are always stored in sorted order.
*/
mpp["tank"] = 89;      // tank: 89 is inserted (sorted by key)
mpp["raj"] = 29;       // raj's value is updated to 29 (unique keys, sorted by key)



mpp.emplace("raj", 45); // raj's value is updated to 45 (unique keys, sorted by key)

mpp.erase("raj"); // removes key "raj"
mpp.erase(mpp.begin()); // removes the first element (smallest key)
mpp.clear(); // entire map is cleaned up
mpp.erase(mpp.begin(), mpp.begin() + 2); // cleans up a given range

auto it = mpp.find("raj"); // points to where raj lies (if exists, at correct sorted position)

if(mpp.empty()) {
    cout << "Yes it is empty";
}

mpp.count("raj"); // always returns 1 as map stores only 1 instance of a key (sorted container)

```


==**PAIR(STL)**==
```cpp
// Pair class basics
pair<int, int> pr = {1, 2};  // single pair: first = 1, second = 2
// Simple pair usage
pr.first = 1;     // assign 1 to first element
pr.second = 2;   // assign 10 to second element

// Nested pair: first is a pair, second is int
pair< pair<int, int>, int> pr2 = {{1, 2}, 2};
cout << pr2.first.second << endl; // prints 2 (second value of inner pair)

// Pair of pairs: both first and second are pairs
pair< pair<int, int>, pair<int, int>> pr3 = {{1, 2}, {2, 4}};
cout << pr3.first.first;    // prints 1 (first value of first pair)
cout << pr3.second.second;  // prints 4 (second value of second pair)

// These STL containers can store pairs:
vector<pair<int, int>> vec;             // vector of pairs
set<pair<int, int>> st;                 // set of pairs (sorted, unique)
map< pair<int, int>, int> mpp;          // map with pair as key, int as value

```

==**printing map**==
```cpp
// printing map
for (auto it : mpp) {
    cout << it.first << " " << it.second << endl;
}

for (auto it = mpp.begin(); it != mpp.end(); it++) {
    cout << it->first << " " << it->second << endl;
}


```

==**UNORDERED MAP AND MULTIMAP**==
```cpp
#include <unordered_map>
// does not stores in any order
unordered_map<int, int> mpp; 
// unordered_map<pair<int,int>, int> mpp; xxxxxx
// o(1) in almost all cases
// o(n) in the worst case, where n is the container size


multimap<string, int> mpp;
mpp.emplace("vipul",2);   or mpp["vipul"]=2;
mpp.emplace("vipul",5);   or mpp["vipul"]=5;
```