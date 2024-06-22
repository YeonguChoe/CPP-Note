# 포인터

| *의 사용처           | &의 사용처                             |
| -------------------- | -------------------------------------- |
| 포인터 변수 생성     | 포인터 변수 생성                       |
| 포인터 dereferencing | 레퍼런스 변수(reference variable) 생성 |

## 포인터 변수 생성

- 포인터 변수는 다른 변수의 메인 메모리에서의 주소를 저장하는 자료형이다.

```CC
int myNumber = 2023;
int *addressOfMyNumber = &myNumber; //참조(referencing)
std::string myText = "C++";
std::string *addressOfMyText = &myText; //참조(referencing)
```

## 포인터 Dereferencing

- 포인터 변수 앞에 *이 붙이면, 포인터 변수가 보관하고 있는 주소에 위치한 변수를
  의미한다. (Dereferencing)

```CC
int myNumber = 2023;
int *myPointer = &myNumber; //참조(referencing)
cout << *myPointer << endl; //역참조(dereferencing)
```

## array 변수의 이름은 array의 첫번째 element의 주소를 의미한다.

- 반면, array변수의 이름 앞에 &를 붙이면, array변수의 주소값을 새로운 포인터에
  설정한 이후, 해당 포인터 변수를 반환 한다.

```CC
int myArray[4] = {1, 9, 6, 2};
myArray; // myArray[0]의 메모리상의 주소
&myArray; // myArray[0]의 주소를 가진 포인터 변수 반환
```

## 포인터 연산 (Pointer arithematic)

- 포인터 변수에 1을 더하면, 해당 주소에서 포인터 변수가 가리키는 변수의 자료형의
  데이터 크기 만큼 더한 다음 주소값을 의미한다.

```CC
int myArray[4] = {1, 9, 6, 2};
myArray + 1; // myArray[1]의 주소
myArray + 2; // myArray[2]의 주소
```

## & 연산자로 포인터 변수 생성

### 변수 앞에 & 연산자를 붙일때 일어나는 일

1. 변수의 메인 메모리상의 주소를 포인터 변수에 설정한다.
2. 해당 포인터 변수를 반환 한다.

```CC
std::string myVariable = "Korea";
std::cout << &myVariable;
```

## 레퍼런스 변수(reference variable)

- 레퍼런스 변수는 자료형이 아니다.
- 이미 존재하는 변수를 참조하는 방법이다.

```CC
int 변수_이름 = 값;
int &레퍼런스_변수 = 변수_이름;
```

# 함수에서 포인터 사용

## 함수에서 pass by reference 방식을 사용해서 실제 변수의 값을 변경하는 방법

- 함수에서 일반적인 pass by value 방식으로는 argument가 함수 안으로 복사가 된다.
  따라서, 실제 변수의 값은 변경 되지 않는다.
- 하지만, pass by reference 방식으로 함수의 parameter을 지정하면, 실제 함수에
  argument로서 입력하는 실제 변수를 수정 한다.

```CC
// Pass by value
// API: argument를 복사해서 함수 안에서 사용하는 함수
void onlyCopyActual(int copyOfArgument) {
    copyOfArgument = 10;
}
// Pass by reference
// API: 실제로 변수를 수정할 수 있는 함수
void changeActual(int &target) {
    target = 1962;
}
```

# 스마트 포인터(Smart pointer)

- 스마트 포인터 변수는 자동으로 Heap 영역에 저장된 변수를 삭제해 주는 변수이다.
- 스마트 포인터를 이용해서 메모리 누수(memory leak)를 방지 할 수 있다.
- 종류
  - std::unique_ptr
  - std::shared_ptr
  - std::weak_ptr

- 스마트 포인터를 사용하려면 memory 라이브러리를 포함 시켜줘야 한다.

```CC
#include <memory>
```

## Unique pointer

- Unique 포인터를 사용하면 1개의 객체가 1개의 포인터만 갖을 수 있게 제한 한다.

### unique 포인터 선언 방법

```CC
std::unique_ptr<클래스_이름> 스마트_포인터_이름 = std::make_unique<클래스_이름>();
```

### unique 포인터를 다른 포인터로 설정하는 방법

```CC
std::unique_ptr<클래스_이름> 새로운_스마트_포인터_이름 = std::move(기존_유니크_포인터_이름);
```

## Shared pointer

- 객체를 가리키는 스마트 포인터 변수의 갯수를 샌다.
- 객체를 가리키는 포인터 변수의 갯수가 0이 되면, Heap에 할당된 객체를 삭제 한다.

### shared 포인터 선언 방법

```CC
std::shared_ptr<클래스_이름> 스마트_포인터_이름 = std::make_shared<클래스_이름>();
```

### 같은 객체를 가리키는 새로운 shared 포인터 선언 방법

```CC
std::shared_ptr<클래스_이름> 새로운_스마트_포인터_이름 = 기존_쉐어드_포인터_이름;
```

### 같은 객체를 가리키는 스마트 포인터 갯수를 반환 받는 방법

```CC
쉐어드_포인터_이름.use_count();
```

### shared 포인터를 삭제하는 방법

```CC
쉐어드_포인터_이름.reset();
```

## Weak pointer

- 객체를 가리키는 포인터 변수의 갯수를 세지 않는다.
- 객체를 다른 포인터에게 위임하고 싶을때 사용한다.

### Weak 포인터 선언 방법

- Weak 포인터는 shared 포인터를 이용해서 선언한다.

```CC
std::shared_ptr<클래스_이름> 쉐어드_포인터_이름 = std::make_shared<클래스_이름>();
std::weak_ptr<클래스_이름> 윅_포인터_이름 = 쉐어드_포인터_이름;
```

### shared pointer에 객체의 소유권을 위임하는 방법

- lock() 함수는 shared_pointer를 반환 한다.

```CC
std::shared_ptr<클래스_이름> 새로운_쉐어드_포인터_이름 = 윅_포인터_이름.lock();
```

# Null 포인터

- nullptr의 값은 0x0이다.
- nullptr의 크기는 8 바이트이다.

## nullptr로 포인터 변수 초기화

```CC
자료형 *포인터_이름 = nullptr;
```

## nullptr로 포인터 변수가 유효한 포인터 변수인지 검사하는 방법

```CC
if (포인터_이름 == nullptr) {
    포인터가_유효하지_않을_때_실행되는_코드
}
```
