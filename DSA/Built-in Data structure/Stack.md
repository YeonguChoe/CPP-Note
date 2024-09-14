# Stack

## Import Statement
```cpp
#include <stack>
```

## Declaring a Stack
```cpp
std::stack<int> x;
```

## Adding element to the Stack
```cpp
x.push(1);
x.push(2);
x.push(3);
x.push(4);
x.push(5);
```

## Removing the topmost element from the Stack
> pop() method does not return removed element
```cpp
x.pop();
```

## Peeking at the topmost element in the Stack
- top() method does not remove element from the Stack
```cpp
x.top();
```

## Checking if the Stack has no elements
```cpp
x.empty();
```

## Number of elements in the Stack
```cpp
x.size();
```

## Exchange every element of two different Stacks
```cpp
std::swap(x, y);
```
