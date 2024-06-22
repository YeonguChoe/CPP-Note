# CLion Build 과정

## Debug 빌드
```bash
cmake -D CMAKE_BUILD_TYPE=Debug -D CMAKE_MAKE_PROGRAM=<경로>/ninja -G Ninja -S <소스코드가 있는 폴더의 경로> -B <파일이 생성되는 폴더의 경로>
```
- `-D`: 변수를 정의(define) 한다.
- [`-D CMAKE_BUILD_TYPE`](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html): 빌드 자동화 도구의 빌드 타입을 지정한다.
- [`-D CMAKE_MAKE_PROGRAM`](https://cmake.org/cmake/help/latest/variable/CMAKE_MAKE_PROGRAM.html): 빌드 자동화 도구의 실행 파일을 지정한다.
- `-B`: CMake가 파일을 생성하는 디렉토리를 지정한다.
- `-S`: CMake가 재료로 사용하는 소스코드 파일의 디렉토리를 지정한다.
- `-S`를 지정 안하면, 현재 작업 디렉토리가 소스 코드의 폴더로 사용된다.
- `-G`는 CMake가 사용할 빌드 자동화 도구를 지정한다.

- 예
```bash
cmake -D CMAKE_BUILD_TYPE=Debug -D CMAKE_MAKE_PROGRAM=/Applications/CLion.app/Contents/bin/ninja/mac/aarch64/ninja -G Ninja -B cmake-build-debug
```

## 실행 파일 빌드
```bash
cmake --build <생성된 빌드 파일이 위치한 경로> --target <add_executable() 또는 add_library()에 있는 <name>> -j <빌드 작업을 할때 사용할 CPU 쓰레드의 수>
```
- `--build`: 빌드 파일이 위치한 경로에서 빌드를 실행 하도록 한다.
- `--target`: CMakeLists.txt에 있는 빌드 대상을 지정한다.
- `-j`: CPU가 병렬로 빌드 작업을 하도록 한다.


