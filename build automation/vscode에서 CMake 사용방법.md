# Visual Studio Code에서 CMake 사용 방법

## 사용방법
1. `CMake Tools` 익스텐션 설치
2. `CMakeLists.txt` 생성
```cmake
cmake_minimum_required(VERSION 3.5) # CMakeLists에 사용된 문법을 사용하기 위한 컴퓨터에 설치되어야 하는 CMake의 최소 버전
project(Algorithm LANGUAGES C CXX) # 프로젝트 이름과 C, C++을 사용함을 명시
set(CMAKE_CXX_STANDARD 11) # C++ 코드의 문법 버전
set(SOURCE_FILES main.cpp) # 소스 코드
add_executable(program ${SOURCE_FILES}) # 생성되는 실행 파일의 이름과 소스 파일
```
3. `>CMake: Quick Start` 실행

## 빌드 단축키
- MacOS: Shift + F5
- Windows: 