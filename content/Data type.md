# 자료형

- int: 0, 1, 100
- float: 3.75
- double: 11.0

## char

### 일반적인 문자 선언 방법

```CC
char firstAlphabet = 'A';
```

### char을 이용해서 문자열을 선언 방법

```CC
char stringMadeOfChar[] = "Character string";
```

### char 포인터변수로 문자열을 선언하는 방법

```CC
char *stringMadeWithCharPointer = "String made with character string";
```

## string 클래스를 이용해서 문자열을 만드는 방법

```CC
#include <string>
int main() {
std::string myString = "String made with string class";
}
```

- bool: true, false
- void

## Array(크기 고정)

### array 선언 방법

```CC
double myArray[3] = {1, 2, 3};
```

### 2D array를 선언하는 방법

```CC
int matrix[3][3] = {{1, 0, 0},
                    {0, 1, 0},
                    {0, 0, 1}};
```

## vector(크기 변환 가능)

- vector는 크기가 동적으로 변하는 반면, array는 크기가 고정됩니다.
- vector는 array보다 다양한 메서드를 제공합니다.

### vector 선언 방법

```CC
vector<자료형> myVector = {1, 2, 3};
```

### vector의 맨 뒤에 값을 추가 하는 방법

```CC
myVector.push_back(<값>);
```

### vector의 맨 뒤에 있는 값을 삭제하는 방법

```CC
myVector.pop_back(); // 맨 뒤의 값 삭제
```

## Priority queue

### 우선큐 선언 방법

```CC
std::priority_queue<자료형, std::vector<자료형>, 비교자> 우선큐_이름;
```

### pair을 element로 갖는 우선큐 선언 방법

```CC
std::priority_queue<std::pair<자료형, 자료형>, std::vector<std::pair<자료형, 자료형>>, 비교자> 우선큐_이름;
```

### 1개의 값을 비교하는 비교자 선언 방법

```CC
struct SingleValueComparator {
    bool operator()(int &SmallerValue, int &BiggerValue) {
        return SmallerValue < BiggerValue; //큰값이 우선순위가 더 높다.
    }
};
```

### pair의 첫번째 값을 비교하는 비교자 선언 방법

```CC
struct PairComparator {
    bool operator()(const std::pair<int, int> &SmallerValue, const std::pair<int, int> &BiggerValue) const {
        return SmallerValue.first > BiggerValue.first; //pair의 첫번째 값이 작은것이 우선순위가 더 높다.
    }
};
```

### 특정 index에 있는 element를 읽는 방법

```CC
myVector.at(2)
```

# Type conversion

- 값의 자료형을 다른 자료형으로 바꾸는 것이다.

## Implicit conversion(automatic conversion)

### 종류 1: 크기가 작은 자료형은 크기가 더 큰 자료형으로 자동으로 변환이 가능하다.

| 자료형 | 크기    |
| ------ | ------- |
| char   | 1 byte  |
| bool   | 1 byte  |
| short  | 2 bytes |
| int    | 4 bytes |
| float  | 4 bytes |
| long   | 8 bytes |
| double | 8 bytes |

```CC
int i = 1; // 4 bytes
double j = i; // 8 bytes
```

### 종류 2: 포인터 변수와 레퍼런스는 서로 자동으로 변환이 가능하다.

#### 포인터 변수에서 레퍼런스로 자동 변환

```CC
int *ptr = new int(1);
int &ref = *ptr;
```

#### 레퍼런스에서 포인터 변수로 자동 변환

```CC
int number1 = 1;
int &ref = number1;
int *ptr = &ref;
```

## Explicit conversion(type casting)

### C style 캐스팅

- 큰 자료형에서 작은 자료형으로 변환을 할때는 trunicate

```CC
int a = 300;
char b = (int) a;
```

### static 캐스팅

```CC
int a = 300;
char b = static_cast<char>(a);
```
