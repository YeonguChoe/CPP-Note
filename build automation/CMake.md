# Cmake 사용법

## 순서
1. "CMakeLists.txt" 파일을 작성한다.
2. 프로그래밍: .cc파일(.cpp)과 .h파일들을 프로젝트 디렉토리에 코딩한다.
3. 프로젝트 디렉토리와 분리된 빌드 디렉토리를 만든다.
4. cmake 명령어를 terminal에 입력하여 빌드 시스템 파일을 생성한다.
```bash
cmake -S <소스코드들이 있는 위치(프로젝트 디렉토리)> -B <결과물 위치(빌드 디렉토리)>
예: cmake -S . -B out/build
```
5. 빌드 디렉토리에 저장된 빌드 시스템 파일을 make 명령어를 terminal에 입력하여 실행 파일 또는 라이브러리를 만든다.

## CMakeLists.txt에 들어갈 내용

### CMake 버전 설정
- 해당 CMakeLists.txt 파일을 읽을수 있는 최소한의 CMake 버전을 지정한다.
- 생략해도 괜찮다.

```bash
cmake_minimum_required(VERSION 3.28.1)
```

### 프로젝트 이름 설정
- 최종으로 완성되는 실행 파일의 이름을 설정한다.

```bash
project(OrbitalStrike)
```

### 변수 선언
- [set()](https://cmake.org/cmake/help/v2.8.12/cmake.html#command:set)

```bash
set(birth_year 1995) # 숫자 변수 선언
set(name "Yeongu") # 문자열 변수 선언
set(isTrue 1) # Boolean 변수 선언
set(my_list "A" "B" "C") # List 변수 선언
set(greeting "Hello ${name}") # 변수를 포함 하는 문자열 변수 선언
```

### 이미 지정된 변수

| 변수 이름                                                                                       | 의미                                                |
| ----------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| [CMAKE_SYSTEM_NAME](https://cmake.org/cmake/help/v2.8.12/cmake.html#variable:CMAKE_SYSTEM_NAME) | 지금 CMake를 실행시키고 있는 컴퓨터의 운영체제 이름 |
| CMAKE_CURRENT_SOURCE_DIR                                                                        | 프로젝트의 절대 경로                                |
| [PROJECT_NAME](https://cmake.org/cmake/help/v2.8.12/cmake.html#variable:PROJECT_NAME)           | 프로젝트 이름                                       |
| [LINK_LIBRARIES](https://cmake.org/cmake/help/v2.8.12/cmake.html#prop_tgt:LINK_LIBRARIES)       | 포함된 모든 라이브러리                              |


### 문자열 출력하기
- [message()](https://cmake.org/cmake/help/v2.8.12/cmake.html#command:message)

```bash
message("Hello world")
message("Birth year: ${birth_year}") # 변수를 포함하는 문자열 출력하기
```

### if문
- [if()](https://cmake.org/cmake/help/latest/command/if.html#comparisons)

#### 문자열 비교

```bash
set(color "붉은색")

if (${color} MATCHES "붉은색")
    message("이것은 붉은색 입니다")
elseif (${color} MATCHES "초록색")
    message("이것은 초록색 입니다")
else ()
    message("이것은 파란색 입니다")
endif ()
```

#### 숫자 비교

```bash
set(integer_number 1)

if (integer_number LESS 0) # <
    message("${integer_number}는 음수 입니다.")
elseif (integer_number EQUAL 0) # ==
    message("${integer_number}는 0 입니다.")
elseif (integer_number GREATER 0) # >
    message("${integer_number}는 양수 입니다.")
endif ()
```

### foreach문
- [foreach()](https://cmake.org/cmake/help/latest/command/foreach.html)

#### 기본 foreach문

```bash
set(myList 100 200 300 400 500)

foreach (element ${myList})
    message(${element})
endforeach ()
```

#### RANGE를 사용하는 foreach문

```bash
foreach (i RANGE 1 10 1) # 시작; 끝(포함); 추가 하는 수
    message(${i})
endforeach ()
```

#### IN을 사용하는 foreach문

```bash
set(myList 100 200 300 400 500)

foreach (element IN LISTS myList)
    message(AUTHOR_WARNING "Value: ${element}")
endforeach ()
```

### while문
- [while()](https://cmake.org/cmake/help/latest/command/while.html)
- while문은 숫자 연산을 사용해야 한다.
- 
```bash
set(counter 1)

while (counter LESS 5)
    message("${counter}번째 반복 입니다.")
    math(EXPR counter "${counter}+1")
endwhile ()
```

### math(): 숫자 연산
- [math()](https://cmake.org/cmake/help/latest/command/math.html)

#### 10을 곱하기
```bash
set(initial_number 10)
message("Input: ${initial_number}")
math(EXPR initial_number "${initial_number}*10")
message("Output: ${initial_number}")
```

### 함수 만들기
#### macro와 function의 차이점
##### 유일한 차이점은 scope의 생성 여부이다.
- macro()는 새로운 scope를 만들지 않는다.
- function()은 함수안에만 존재하는 새로운 스코프를 만든다.

### macro를 이용한 함수
- [macro()](https://cmake.org/cmake/help/latest/command/macro.html)

#### 3개의 숫자를 더하는 함수
```bash
# 함수명 매개변수1 매개변수2 매개변수3 반환변수
macro(adding_three_numbers num1 num2 num3 output)
    # num1, num2, num3의 합을 output 매개 변수에 할당
    math(EXPR ${output} "${${num1}}+${${num2}}+${${num3}}")
    # 출력
    message("${num1}+${num2}+${num3}=${result}")
endmacro()

# 변수 선언
set(A 1)
set(B 2)
set(C 3)
set(result 0)

# 함수 호출
adding_three_numbers(A B C result)

# 변경된 변수 출력
message(${result})
```

### function을 이용한 함수
- [function()](https://cmake.org/cmake/help/latest/command/function.html)

#### 3개의 숫자를 곱하는 함수
```bash
function(multiply_three_numbers num1 num2 num3 output)
    # local 변수 temp를 만든다.
    set(temporary_variable 0)
    # temporary_variable는 function 안에서만 존재하는 변수이다.
    math(EXPR temporary_variable "${num1} * ${num2} * ${num3}")
    # Parent 스코프에 있는 output에 값을 대입한다.
    set(${output} ${temporary_variable} PARENT_SCOPE)
endfunction()

# 변수를 선언 한다.
set(A 3)
set(B 4)
set(C 5)
set(result 0)  # Initialize the output variable

# 함수를 호출 한다.
multiply_three_numbers(${A} ${B} ${C} result)

# 출력
message("${A}×${B}×${C}=${result}")
```

### 파일 경로들을 포함하는 리스트 만들기
- 파일 경로를 저장하는 리스트는 set으로 만들면 사용할 수 없다.
-  [file(GLOB)](https://cmake.org/cmake/help/latest/command/file.html#glob)

```bash
file(GLOB file_list src/*.cc src/*.hpp)
```

### 파일에 내용 입력하기 (새로운 파일 생성하기)
- [file(WRITE)](https://cmake.org/cmake/help/latest/command/file.html#write)
- 만약에 파일이 존재 하지 않으면, 새로운 파일을 만든다.

#### note.txt 파일에 Hello World라고 쓰기
```bash
file(WRITE note.txt "Hello world")
```

### 새로운 디렉토리 만들기
- [file(MAKE_DIRECTORY)](https://cmake.org/cmake/help/latest/command/file.html#make-directory)

#### 비둘기와 참새 디렉토리 만들기

```bash
file(MAKE_DIRECTORY 비둘기 참새)
```

### 파일 또는 디렉토리 복사하기
- [file(COPY)](https://cmake.org/cmake/help/latest/command/file.html#copy)

#### note.txt 파일을 Desktop 디렉토리에 복사

```bash
file(COPY note.txt DESTINATION Desktop)
```

#### Desktop 디렉토리를 Downloads 디렉토리에 복사

```bash
file(COPY Desktop DESTINATION Downloads)
```

### 디렉토리 삭제하기
- [file(REMOVE_RECURSE)](https://cmake.org/cmake/help/latest/command/file.html#remove-recurse)

#### 비둘기와 참새 디렉토리 삭제

```bash
file(REMOVE_RECURSE 비둘기 참새)
```

### 실행 파일 만들기
- 결과물로 나오는 실행 파일과 해당 실행 파일을 만드는 재료가 되는 소스 코드 파일들을 설정해 주어야 한다.
- [add_executable](https://cmake.org/cmake/help/latest/command/add_executable.html)

```bash
add_executable(${PROJECT_NAME} ${file_list})
```

### 라이브러리 파일 만들기
- 결과물로 나오는 라이브러리 파일과 해당 라이브러리를 만드는 재료가 되는 소스 코드 파일들을 설정해 주어야 한다.
- [add_library()](https://cmake.org/cmake/help/latest/command/add_library.html)

```bash
add_library(${PROJECT_NAME} source_file.cc)
```

### 다른 cmake 모듈 가져오기
- 자바에서 import와 같다.
- [include()](https://cmake.org/cmake/help/latest/command/include.html)
- 모듈을 가져오 다른 cmake 모듈에 있는 function 또는 macro를 사용할 수 있다.

```bash
include(arithematic_module.cmake)
```

### 헤더 파일과 라이브러리 파일
- 헤더 파일은 함수와 클래스의 선언문을 포함한다.
- 라이브러리 파일은 헤더 파일에 선언된 함수나 클래스에 대한 실제 implementation이다.
- 따라서 헤더 파일을 include_directories()로 추가 시켰으면, link_directories()로 라이브러리 파일도 반드시 추가 시켜주어야 한다.


### CMake가 헤더 파일을 찾는 디렉토리 추가

```bash
include_directories(desktop downloads)
```

### target
- 타깃은 cmake에서 생성되는 실행파일 또는 라이브러리를 말한다.

### 특정 target만 헤더 파일을 찾는 디렉토리를 추가하는 방법
- [include_directores와 차이점](https://stackoverflow.com/questions/31969547/what-is-the-difference-between-include-directories-and-target-include-directorie)

```bash
target_include_directories(${PROJECT_NAME} PUBLIC HOME) # HOME 디렉토리에서 헤더 파일을 찾는다
```

### 라이브러리 파일
- 라이브러리 파일의 확장자는 운영체제 마다 다르다.

| 운영체제 | Dynamic 라이브러리 확장자 | Static 라이브러리 확장자 |
| -------- | ------------------------- | ------------------------ |
| Windows  | .dll                      | .lib                     |
| MacOS    | .dylib                    | .a                       |
| Linux    | .so                       | .a                       |

#### Static 라이브러리
- 컴파일 되고 난후 실행파일안에 존재한다.
- 실행파일 안에 포함 되어 있다.

#### Dynamic 라이브러리
- 실행파일 밖에 따로 존재한다.
- 실행파일 안에 포함 시킬 수 없다.

### 라이브러리 파일을 찾는 디렉토리 추가
- CMakeList.txt 안에 있는 모든 target들이 사용할수 있다.
- [link_libraries](https://cmake.org/cmake/help/latest/command/link_libraries.html)

```bash
link_libraries(Desktop/libraries)
```
### 특정 target만 라이브러리 파일을 찾는 디렉토리 추가
- link_libraries 보다 최신의 기술이다.
- [target_link_libraries](https://cmake.org/cmake/help/latest/command/target_link_libraries.html)

```bash
target_include_directories(${PROJECT_NAME} PUBLIC src/graphics-library src/music-library)
```

### 시스템을 뒤져서 라이브러리 찾기

#### 방법1. find_package를 사용해서 라이브러리 찾기
- [find_package](https://cmake.org/cmake/help/latest/command/find_package.html)
- find_package는 Windows, MacOS, Linux 모두에서 다 사용 될 수 있다.

##### OpenGL을 찾기

```bash
find_package(OpenGL REQUIRED)
```

##### 찾은 OpenGL의 라이브러리 경로를 추가한다

```bash
if (OPENGL_FOUND)
    target_link_libraries(${PROJECT_NAME} PUBLIC ${OPENGL_gl_LIBRARY})
endif ()
```

#### 방법2. PkgConfig를 사용해서 라이브러리 찾
- MacOS와 Linux에서는 PkgConfig를 이용해서 시스템에 설치된 라이브러리를 찾을 수도 있다.

```bash
find_package(PkgConfig REQUIRED)

pkg_search_module(OpenGL REQUIRED opengl)

# 헤더 디렉토리 추가
target_include_directories(${PROJECT_NAME} PUBLIC ${OpenGL_INCLUDE_DIRS})

# 라이브러리 디렉토리 추가
target_link_libraries(${PROJECT_NAME} ${OpenGL_LIBRARIES})
```


---

# 추가 할 내용
FetchContent: https://cmake.org/cmake/help/latest/module/FetchContent.html
find_library: https://cmake.org/cmake/help/latest/command/find_library.html
