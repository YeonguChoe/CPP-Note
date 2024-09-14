# Unordered Map
- `unordered_map` is the same as Hash Map
- Unlike `Map`, `Unordered Map` does not maintain the order of `{key,value}` pair

## Import Statement
```cpp
#include <unordered_map>
```

## Declaring a Hash Map
```cpp
// Basic
std::unordered_map<int, char> x;

// Initializing elements
std::unordered_map<int, char> y = { {65,'A'},{66,'B'},{67,'C'} };
```

## Accessing element in the Hash Map
### Using at() method
- at() method returns 
```cpp
// Accessing a pair whose key is 97
x.at(97);

// Pointer variable storing address of a pair whose key is 97
char* pt = &x.at(97);
```

### Using subscript operator
```cpp
// Accessing a pair whose key is 97
x[97];

// Pointer variable storing address of a pair whose key is 97
char* pt = &x[97];
```

## Adding element to the Hash Map
### Using subscript operator
```cpp
x[65] = 'A';
```

### Using insert() method
```cpp
x.insert({ 97,'a' });
x.insert({ 98,'b' });
x.insert({ 99,'c' });
```

## Removing element from the Hash Map
```cpp
// Removing a {key, value} pair whose key is 97
x.erase(97);
```

## How to iterate over Hash Map
- .first represents key of the pair
- .second represents value of the pair
```cpp
for (auto pair : x)
{
    std::cout << pair.first << ":" << pair.second << std::endl;
}
```

## Checking if the Hash Map is empty
```cpp
x.empty();
```
