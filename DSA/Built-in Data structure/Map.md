# Map
- Unlike `unordered map`, pairs are sorted in ascending order of keys

## Import Statement
```cpp
#include <map>
```

## Declaring a Map
```cpp
// basic
std::map<char, int> x;
// Initializing element
std::map<char, int> y = {
    {'a',97},{'b',98},{'c',99}
};
```

## Adding element to the Map
```cpp
// Adding subscriptor operator
x['e'] = 101;
x['f'] = 102;
// Using insert() method
x.insert({ 'g',103 });
```

## Accessing element in the Map
```cpp
// Using subscriptor operator
x['a'];

// Using at(<key>) method
// at() method returns a reference to value of the pair
x.at('a');
```

## Printing every element in the Map
```cpp
for (auto pair : x)
{
    std::cout << pair.first << ":" << pair.second << std::endl;
}
```

## Removing element from the Map
```cpp
// Using erase(key) method
x.erase('a');

// Clearing out the Map
x.clear();
```

## Number of pair in the Map
```cpp
// Number of pairs in the Map
x.size();
// Checking if the Map is empty
x.empty();
```

