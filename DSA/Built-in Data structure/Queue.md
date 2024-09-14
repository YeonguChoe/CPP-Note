# Queue

## Import Statement
```cpp
#include <queue>
```

## Declaring a Queue
### Basic
```cpp
std::queue<int> x;
```

### Simultaneously initializing element
```cpp
std::queue<int> x({ 1,2,3,4,5 });
```

## Adding element to the back of the Queue
```cpp
x.push(1);
x.push(2);
x.push(3);
x.push(4);
x.push(5);
```

## Removing element at the front of the Queue
> pop() method does not return value of the removed element
```cpp
x.pop();
```

## Exchanging every element of two different Queues
```cpp
std::swap(x, y);
```

## Getting element at the front of the Queue
>front() method returns a reference to the front most element of the Queue
```cpp
x.front();
```

## Getting element at the back of the Queue
>back() method returns a reference to the back most element of the Queue
```cpp
x.back();
```

## Getting address of the front most element of the Queue
```cpp
int* pt = &x.front();
```

## Getting address of the rear most element of the Queue
```cpp
int* pt = &x.back();
```

## Number of elements in the Queue
```cpp
x.size();
```

## Checking if the Queue is empty
```cpp
x.empty();
```
