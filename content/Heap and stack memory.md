## 메인 메모리의 힙 영역에 변수를 저장 하는 방법

### 일반적인 변수 선언은 스택 영역에 저장된다.

- 동적 할당을 사용하지 않고 일반적으로 선언한 변수들은 스택 메모리에 저장됩니다.
- 스택 메모리는 지역 변수를 저장하는 데 사용되는 메모리 영역입니다.
- 지역 변수는 함수가 호출될 때 생성되고 함수가 종료될 때 소멸됩니다.

### new와 delete 키워드를 사용해서 힙 영역에 변수를 선언 할수 있다.

- 동적 할당을 사용하면 힙 메모리에 변수를 할당할 수 있습니다.
- 힙 메모리는 스택 메모리보다 크기가 크고, 함수의 종료와 관계없이 변수를 유지할
  수 있습니다.
- 힙 메모리는 동적으로 할당하고 해제해야 합니다.

### Heap 영역에 변수를 저장하는 방법

```CC
int *pointerToVariableInHeap = new int; // new 키워드로 int의 크기 만큼 heap 영역에 공간을 만들고, 해당 위치의 주소를 포인터 변수에 저장
delete pointerToVariableInHeap; // 포인터 변수가 가지고 있는 주소에 위치한 변수를 heap 영역에서 삭제 한다.
```

### Heap 영역에 array를 저장하는 방법

```CC
int *pointerToArrayInHeap = new int[4]; // array를 heap 영역에 할당
*(pointerToArrayInHeap) = 1;
*(pointerToArrayInHeap + 1) = 9;
*(pointerToArrayInHeap + 2) = 6;
*(pointerToArrayInHeap + 3) = 2;
delete[] pointerToArrayInHeap; // Heap 영역에 할당한 array를 삭제
```

# Dynamic allocation (Heap allocation)

- Heap 영역에 객체를 만든다.

## Heap 영역에 객체를 저장하는 방법

```CC
// 객체 선언
class myClass {
public:
    int myVariable = 0;
    void myFunction() {
        std::cout << "My Function" << std::endl;
    }
};

int main() {
    myClass *객체_포인터 = new myClass(); // Heap 영역에 객체 할당
```

## Heap 영역에 저장된 객체 안의 변수를 조회 또는 수정 하는 2가지 방법

```CC
(*객체_포인터).myVariable; // 방법 1
객체_포인터->myVariable; // 방법 2
```

## Heap 영역에 저장된 객체안의 함수를 호출하는 2가지 방법

```CC
(*객체_포인터).myFunction(); // 방법 1
객체_포인터->myFunction(); // 방법 2
```

# Stack allocation

- Stack영역에 객체를 만든다.

```CC
myClass mc; // argument가 없는 default constructor을 호출하는 경우
myClass mc2(3); // argument가 있는 constructor을 호출하는 경우
```


## Heap에 생성된 객체를 삭제하는 방법

- Heap에 생성된 객체는 자동으로 삭제 되지 않기 때문에 객체를 직접 삭제 해 줘야
  한다.

```CC
delete 객체_포인터; // Heap 영역에 저장된 객체 삭제
```