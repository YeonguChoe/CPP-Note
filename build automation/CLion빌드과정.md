# CMake 빌드 명령어

## CMake 빌드 순서
$$
\text{CMakeLists.txt 작성}\longrightarrow\text{빌드 시스템 생성 (Ninja)}\longrightarrow\text{실행 파일 또는 라이브러리 생성}
$$

## 빌드 시스템 종류
- Debug 빌드
- Release 빌드
- Release With Debug Information
- Minimum Size Release

### 실행 파일 크기
$$ \text{MinSizeRel} < \text{Release} < \text{RelWithDebInfo} < \text{Debug}$$

### Debug 빌드
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
    cmake -D CMAKE_BUILD_TYPE=Debug -D CMAKE_MAKE_PROGRAM=/Applications/CLion.app/Contents/bin/ninja/mac/aarch64/ninja -G Ninja -S . -B cmake-build-debug
    ```

### Release 빌드
```bash
cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_MAKE_PROGRAM=/Applications/CLion.app/Contents/bin/ninja/mac/aarch64/ninja -G Ninja -S . -B cmake-build-release
```
- 디버깅 정보를 아예 포함하지않고 최적화된 빌드를 한다.

### Default 빌드
```bash
cmake -D CMAKE_MAKE_PROGRAM=/Applications/CLion.app/Contents/bin/ninja/mac/aarch64/ninja -G Ninja -B cmake-build-default
```
- 빌드 타입을 지정하지 않으면 Release 빌드를 한다.

### Release With Debug Information 빌드
```bash
cmake -D CMAKE_BUILD_TYPE=RelWithDebInfo -D CMAKE_MAKE_PROGRAM=/Applications/CLion.app/Contents/bin/ninja/mac/aarch64/ninja -G Ninja -S . -B cmake-build-relwithdebinfo
```
- 디버그 정보를 포함하는 최적화된 Release 빌드를 한다.

### Minimum Size Release 빌드
```bash
cmake -D CMAKE_BUILD_TYPE=MinSizeRel -D CMAKE_MAKE_PROGRAM=/Applications/CLion.app/Contents/bin/ninja/mac/aarch64/ninja -G Ninja -S . -B cmake-build-minsizerel
```
- 필요한 모든 기능들을 포함하면서, 실행 파일의 크기를 최소로 하는 빌드를 한다.


## 실행 파일 또는 라이브러리 생성
```bash
cmake --build <생성된 빌드 파일이 위치한 경로> --target <add_executable() 또는 add_library()에 있는 <name>> -j <빌드 작업을 할때 사용할 CPU 쓰레드의 수>
```
- `--build`: 빌드 파일이 위치한 경로에서 빌드를 실행 하도록 한다.
- `--target`: CMakeLists.txt에 있는 빌드 대상을 지정한다.
- `-j`: CPU가 병렬로 빌드 작업을 하도록 한다.

- 예
    ```bash
    cmake --build cmake-build-release --target HelloWorld -j 6
    ```