# Header 파일(.h 파일)

- 헤더 파일은 .cpp 파일들간을 연결해 주는 역할을 한다.

## Header 파일 작성 방법

- 헤더 파일에는 주로 함수의 signature만 작성해 준다.
- 헤더 파일에는 변수, 함수, 클래스, 구조체가 들어갈수 있다.

```CC
#pragma once

// 전처리기
#include <iostream>

//변수 선언
int variableInHeaderFile = 0;

//signature만 있는 함수
void simpleFunction();

//구현부가 있는 함수
void functionWithImplementation() {
    std::cout << "Implementation in Header file" << std::endl;
}

//signature만 있는 클래스
class simpleClass;

//구현부가 있는 클래스
class classInHeaderFile {
public:
    int myVariable = 0;
};

//signature만 있는 구조체
struct simpleStruct;

//구현부가 있는 구조체
struct structWithImplementation {
    int structValue = 0;

    void structFunction() {
        std::cout << "This is function in the structure" << std::endl;
    }
};
```

- 헤더파일을 include하는 모든 .cpp 파일에서 헤더파일에 선언된 함수들을 사용할 수
  있다.

```CC
#include "myHeader.h"
```
