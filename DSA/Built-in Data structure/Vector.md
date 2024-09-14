# Vector
- Size changes dynamically

## Import Statement
```cpp
#include <vector>
#include <algorithm>
#include <random>
```

## Declaring a Vector
### Basic Declaration
```cpp
std::vector<int> x = { 1,2,3,4,5 };
```

### Declaring a Vector where each element is default value
```cpp
std::vector<int> x(5);
```

### Declaring a Vector with size and initial element
```cpp
// {1,1,1,1,1}
// size of the vector: 5
// value of every element: 1
std::vector<int> x(5, 1);
```

## Adding element to the Vector
```cpp
x.push_back(1);
x.push_back(2);
x.push_back(3);
```

## Accessing element from the Vector
### Using Subscript Operator
```cpp
x[1] = 100;
```

### Using at() method
```cpp
// Accessing element at index 1
x.at(1);
```

## Address at the beginning of the Vector
```cpp
x.begin()
```
## Address at the end of the Vector allocation
```cpp
x.end();
```

- end() method does not return the starting address of the last element in the Vector
- end() method returns the address of the exact end of vector allocation

<img src="https://upload.cppreference.com/mwiki/images/1/1b/range-begin-end.svg">

## Removing element from the Vector
- 1st parameter of erase method is the starting address of memory to be removed
- 2nd parameter of erase method is the exact ending address of memory to be removed

```cpp
// Removing the first 2 elements from the vector
x.erase(x.begin(), x.begin() + 2);
```

## Clearing out the vector
```cpp
x.clear();
```

## Number of elements existing within the Vector
```cpp
x.size();
```

## Number of capacity that the Vector can store without reallocation
- Capacity of the Vector changes based on built-in memory management strategy
```cpp
x.capacity();
```

## List Comprehension with Lambda Expression
> Algorithm library is required to use lambda function

```cpp
// power every element by 2
std::vector<int> x = { 1,2,3,4,5 };
int i = 0;
std::generate(x.begin(), x.end(), [&]() mutable {
    int value = x[i++];
    return value * value; });
```

## Sorting the Vector
```cpp
// Ascending order
std::sort(x.begin(), x.end());

// Descending order
std::sort(x.rbegin(), x.rend());
```

## Reversing the order of the Vector
```cpp
std::reverse(x.begin(), x.end());
```

## Shuffling the order of the Vector
```cpp
std::random_device rd;
std::mt19937 gen(rd());
std::shuffle(x.begin(), x.end(), gen);
```