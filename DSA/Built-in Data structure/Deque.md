# Double-ended queue

## Import Statment
```cpp
#include <deque>
```

## Declaring a Deque
```cpp
// Empty Deque
std::deque<int> x;

// Initializing a Deque with value
std::deque<int> y = { 1,2,3,4,5 };
std::deque<int> z{1, 2, 3, 4, 5};
```

## Adding element at the beginning of the Deque
```cpp
x.push_front(1);
```

## Adding element at the end of the Deque
```cpp
x.push_back(1);
```

## Removing element from the beginning of the Deque
```cpp
x.pop_front();
```

## Removing element from the end of the Deque
```cpp
x.pop_back();
```

## Accessing element at the front of the Deque
```cpp
x.front();
```

## Accessing element at the back of the Deque
```cpp
x.back();
```

## Removing element at specific index in the Deque
<img src="https://upload.cppreference.com/mwiki/images/1/1b/range-begin-end.svg">

```cpp
// Removing element at index 1
x.erase(x.begin() + 1);

// Removing element at the end of the Deque
// end() method returns index after end of deque, so it is x.end()-1
x.erase(x.end() - 1);
```

## Removing every element from the Deque
```cpp
x.clear();
```

## Getting a reference to the beginning of the Deque
> front() method returns a reference to the front most element of the Queue
```cpp
// Changing the value at the beginning of the deque
x.front() = 1;

// Pointer to the element at the beginning of the Deque
int* pt = &x.front();
*pt = 2;
```

## Getting a reference to the end of the Deque
> back() method returns a reference to the back most element of the Queue
```cpp
x.back();
```

## Getting a pointer to a specific index
```cpp
int index = 1;
int* pt = &x.at(index);
```

## Number of elements in the Deque
```cpp
x.size();
```

## Checking if the Deque is empty
```cpp
x.empty();
```
