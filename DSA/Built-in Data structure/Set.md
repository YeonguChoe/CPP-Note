# Set
- Set maintains order of element, because it is implemented with binary search tree (Red-black tree)

## Import Statement
```cpp
#include <set>
```

## Declaring a Set
```cpp
// Basic
std::set<int> x;

// Initializing element
std::set<int> y = { 1,2,3,4,5 };
std::set<int> z{ 1,2,3,4,5 };
```

## Adding element to the Set
```cpp
x.insert(1);
x.insert(2);
x.insert(3);
```

## Removing element from the Set
```cpp
// Removing specific element from the Set
x.erase(1);

// Clearing out the set
x.clear();
```

## Number of element in the Set
```cpp
// Number of elements in the Set
x.size();

// Checking if the Set is empty
x.empty();
```

## Getting iterator pointing to specific element in the Set
- If the element does not exist in the Set, find() method returns end()
```cpp
x.find(1);
```

## Exchanging every element of two different Sets
```cpp
std::set<int> x{ 1,2,3,4,5 };
std::set<int> y{ 6,7,8,9,10 };
// Exchanging elements of two different sets
std::swap(x, y);
```
