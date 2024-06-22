# Make 사용법

## **기본 C++ 컴파일 명령어**
![컴파일 순서](/src/compile%20process.png)

### C++ 소스코드 파일을 Assembly 언어까지 컴파일
```CC
clang++/g++ -S <소스파일.cc>
```
### Assembly 파일을 오브젝트 파일(기계어 파일)로 컴파일
```CC
clang++/g++ -c <소스파일.s>
```
### 한번에 실행 파일까지 컴파일
```CC
clang++/g++ <소스파일.cc> -o <결과물 실행파일 이름>
```
### 여러개의 오브젝트 파일을 링킹해서 한개의 결과물 실행 파일로 컴파일
![링킹](/src/linking.png)
```CC
clang++/g++ <오브젝트 파일1> <오브젝트 파일2> <오브젝트 파일3> -o <결과물 실행 파일> -l <외부 라이브러리>
# 외부 라이브러리를 사용할 때만 -l을 사용한다.
```
---

## Makefile의 레시피 구조
```MakeFile
Target(목표 결과물): Dependency(재료 파일)
    Action(컴파일 명령어)
```
최종 목표 결과물을 먼저 적어준다. 그리고 재료 파일들을 만드는 순서대로 적어 준다.
```MakeFile
geom: geom.o gd.o
    clang++ geom.o gd.o -o geom -l <라이브러리 이름>

geom.o: geom.cc gd.h
    clang++ -c geom.cc

gd.o: gd.cc
    clang++ -c gd.cc

tip: gd.o tip.o
    clang++ gd.o tip.o -o tip

tip.o: tip.cc gd.h
    clang++ -c tip.cc
```

## 특수 MakeFile 레시피
```MakeFile
# 전체 실행
all: geom tip

# 오브젝트 파일과 실행 파일을 삭제한다.
clean:
    rm *.o geom tip
```

## 변수 설정
* 변수는 대문자 알파벳과 밑줄을 사용해서 정의한다.
```MakeFile
CC = clang++
```

## 변수 사용
* 변수를 사용할때는 '$'를 앞에 붙여주고 괄호로 묶는다.
```MakeFile
theProject: main.cc
    $(CC) -o theProject main.cc
```