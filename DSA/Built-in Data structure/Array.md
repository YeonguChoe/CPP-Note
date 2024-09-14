# Array

## Import Statement
```
#include <algorithm>
```

## Declaring an Array

### Explicit size
```cpp
int x[5] = { 0,0,0,0,0 };
```

### Implicit size
```cpp
int x[] = { 0,0,0,0,0 };
```

## Accessing element in the Array

```cpp
x[1];
```

## Getting number of elements in the Array
```cpp
sizeof(x) / sizeof(x[0]);
```

## Sorting the Array
### Ascending order
```cpp
std::sort(x, x + sizeof(x) / sizeof(x[0]));
```

### Descending order
```cpp
std::sort(x, x + sizeof(x) / sizeof(x[0]), std::greater<int>());
```