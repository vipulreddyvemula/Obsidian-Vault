==**Stack**== :- it is nothing but last in first out(lifo)  data structure
```cpp
//stack     //0(1)
stack<int> st;  //lifo ds
//pop
//top
//size
//empty
//push and emplace

st.push(2);//container looks like this//|   1   |
st.push(4);                          // |   3   |
st.push(3);                          // |   4   |
st.push(1);                        //   |   2   |goes in down direction
	                                //  |_______|                
cout << st.top();  //prints 1
st.pop();         //deletes the last entered element
cout << st.top();  //prints 3

bool flag = st.empty();  //returns true if stack is empty

//deletes the entire stack  //linear time
while(!st.empty()){
	st.pop();
}

cout << st.size() << endl;  // number of elemnets in the stack

stack<int> st;
if(!st.empty()) {
	cout << st.top() << endl;  //throw error
}
```


==**Queue**== :- first in first out operation(fifo) data structure
```cpp
//queue
queue<int> q;
//push
//front
//pop
//size
//empty

q.push(1);//container looks like this//  |   6   |
q.push(5);                           //  |   3   |
q.push(3);                           //  |   5   |
q.push(6);                           //  |   1   |goes in up direction
                                     //  |_______| 
cout << q.front(); // prints 1
q.pop();
cout << q.front(); // prints 5

// linear time 0(n) //deletes the entire stack 
while(!q.empty()) {
    q.pop();
}

//iterators dont exist in stack and queue
queue<int> q;
for(int i = 0;i<10;i++) q.push(i); 

```

==**Priority Queue**== :- It is like a ordered set(but repetitions are possible) and is sorted but can access only highest priority element is possible
```cpp
// priority_queue 
// push 
// size 
// top pop empty 
priority_queue<int> pq;
q.push(1);//container looks like this//  |   6   |
q.push(5);                           //  |   5   |
q.push(2);                           //  |   2   |
q.push(6);                           //  |   1   |goes in up direction
                                     //  |_______| 
cout << pq.top(); // print 6 
pq.pop(); 
cout << pq.top(); // print 5 

// For pair<int, int>
    priority_queue<pair<int, int>> pq2;
    pq2.push({1, 5});
    pq2.push({1, 6});
    pq2.push({1, 7});
    // The container now looks like:
    // (1,7)
    // (1,6)
    // (1,5)
//min priority queue using the above method
priority_queue<int> pq;
pq.push(-1); // pq.push(-1 * el);
pq.push(-5);
pq.push(-2);
pq.push(-6);

cout << -1 * pq.top() << endl; // prints 1

// min priority queue using the actual syntax method
priority_queue<int, vector<int>, greater<int>> pq;
pq.push(1);
pq.push(5);
pq.push(2);
pq.push(6);

cout << pq.top() << endl; // prints 1
//min pair priority queue actual syntax method
priority_queue<pair<int,int>, vector<pair<int,int>>, greater<pair<int,int>>> pq;

```

==**dequeue**== :- linear data structure that allows efficient insertion and deletion of elements at both the front and the rear ends.
```cpp
dequeue<int> dq; 
// push_front() 
// push_back() 
// pop_front() 
// pop_back()
// begin, end, rbegin, rend 
// size 
// clear
// empty 
// at 

```

==**List**== :- Best when you need to frequently insert or erase elements in the middle 
```cpp
list<int> ls; 
// push_front() 
// push_back() 
// pop_front() 
// pop_back()
// begin, end, rbegin, rend 
// size 
// clear
// empty 
// at 
// remove -> O(1) 
ls.push_front(1); 
ls.push_front(2); 
ls.push_front(3);
ls.remove(2); -> // o(1) operation 
```

| Feature                | list (std::list)           | deque (std::deque)      |
| ---------------------- | -------------------------- | ----------------------- |
| Implementation         | Doubly linked list         | Dynamic array of chunks |
| Random Access          | No                         | Yes                     |
| Insert/Delete Anywhere | Fast (O(1)O(1)O(1))        | Slow (O(n)O(n)O(n))     |
| Insert/Delete at Ends  | Fast (O(1)O(1)O(1))        | Fast (O(1)O(1)O(1))     |
| Memory Layout          | Nodes dispersed in memory  | Contiguous blocks       |
| Iterator Validity      | Preserved (except removed) | May invalidate          |