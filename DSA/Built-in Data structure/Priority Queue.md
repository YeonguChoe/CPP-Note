# Priority Queue
> Built-in Priority Queue is Max Heap by default

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c4/Max-Heap-new.svg/800px-Max-Heap-new.svg.png">

## Import Statement
```cpp
#include <queue>
```

## Declaring a Max Heap
```cpp
std::priority_queue<int> x;
```

## Declaring a Min Heap
```cpp
std::priority_queue<int, std::vector<int>, std::greater<int>> x;
```

## Adding element to the Heap
```cpp
x.push(1);
```

## Removing top most element from the Heap
```cpp
x.pop();
```

## Peeking the top most element of the Heap
- top() method doesn't remove the top most element from the Heap

```cpp
// Accessing the top most element
x.top();
```

- top() method returns reference to the top most element of the Heap
> Unlike front() method of the `queue`, it is impossible to directly make pointer variable with top() method, because of implementation

### How to make pointer to the top element of the Heap
```cpp
// Creating a pointer to the top element of the Heap
// 1. assign value of reference to a variable
int temp = x.top();
// 2. declare a pointer variable and assign the value
int* pt = &temp;
```

## Exchanging every element of two different Heaps
> Two target Heaps should have the same structure

> Elements of Max Heap and Min Heap cannot be exchanged

```cpp
std::priority_queue<int, std::vector<int>, std::greater<int>> x;
x.push(1);
x.push(2);
x.push(3);
x.push(4);
x.push(5);

std::priority_queue<int, std::vector<int>, std::greater<int>> y;
y.push(6);
y.push(7);
y.push(8);

std::swap(x, y);
```

## Number of elements in the Heap
```cpp
x.size();
```

## Checking if the Heap is empty
```cpp
x.empty();
```