# MacOS에서 CMake 설치하는 방법
1. https://cmake.org/download/ 에서 `Unix/Linux Source` source distribution 다운로드
2. `tar -xzvf cmake-3.30.2.tar.gz`로 압축 풀기
3. `cd cmake-3.30.2`: 디렉토리로 이동
4. `./bootstrap`: CMake 소스코드를 시스템에 맞게 설정
5. `make`: 소스코드를 컴파일하여 실행파일과 라이브러리를 만듬
6. `sudo make install`: 빌드된 실행파일과 라이브러리를 시스템에 설치


