# LLDB 사용법
* Low Level virtual machine DeBugger의 약자이다.

# 순서
1. 다음 명령어로 디버깅 정보가 포함된 코드를 생성한다.
```bash
# clang++로 컴파일 한 경우
# -g는 디버깅 정보를 포함혀어 컴파일 한다는 것이다.
clang++ -g <소스 코드 이름>
# 결과: a.out 파일이 생성된다.
```
```bash
# CMake로 컴파일 한 경우
cmake -DCMAKE_BUILD_TYPE=Debug <소스코드 파일 위치>
# 결과: <실행파일 이름> 파일이 생성된다.
# 같은 효과로, CMakeLists.txt 파일에
set(CMAKE_BUILD_TYPE Debug)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g")
# 를 추가해 줘도 된다.
```
2. clang++ -g로 생성된 경우 a.out 파일을, cmake로 만들어진 경우 <실행파일>을, argument와 함께 lldb 명령어로 실행한다.
```bash
# clang++로 컴파일 된 경우
lldb -- a.out <argument1> <argument2> ...
```
```bash
# cmake로 컴파일 된 경우
lldb <실행파일 이름> <argument1> <argument2> ...
```
3.1 Breakpoint 설정
```bash
# 지정한 줄에서 멈춘다.
break set -f <소스코드 파일 이름> -l <줄 번호>
또는
b <소스코드 파일 이름>:<줄 번호>
또는
# 함수가 시작 하는 지점에서 멈춘다.
b <함수 시그니처>
```
3.2 Breakpoint 나열하기
```bash
break list
```
3.3 Breakpoint 제거
```bash
break delete <설정한 breakpoint 번호>
```

4. 코드 실행
```bash
run 또는 r
```
5. 이동하기
```bash
# next: 다음줄로 이동 (Step over)
# stepi: 함수 안으로 이동 (Step in)
# continue: 다음 breakpoint로 이동
# frame select: 현재 위치를 보여준다.
```
6. 변수값 보기
6.1 생성된 모든 변수 보기
```bash
frame variable
```
6.2 변수에 assign된 값 보기
```bash
print <변수 이름>
```
6.3 디버그 도중에 변수값을 바꾸기
```bash
expression <변수 이름> = <새로운 변수값>
```
7. Back trace
* 함수를 호출한 call stack을 보여준다.
```bash
# main을 시작으로 위로 함수가 쌓여 간다.
bt
```
7.1 다른 프레임 안에 있는 변수들을 보기 위해 프레임을 바꾸기
```bash
frame select <프레임 번호>
```
8. Watchpoint 설정
* 디버깅 중에 watchpoint는 변수나 메모리 위치의 값을 계속해서 확인하면서, 값이 변경되는 순간에 디버거가 자동으로 breakpoint를 설정하도록 하는 기능입니다.
```bash
watchpoint set variable <변수 이름>

# watchpoint 변수가 읽어질 때 break
watchpoint set variable <변수 이름> --watch read

# watchpoint 변수값이 변경될 때 break
watchpoint set variable <변수 이름> --watch write
```
8.1 Watchpoint로 설정한 변수 값이 변경 될때 마다 break가 걸린다.
```bash
# continue를 할때 watchpoint로 설정한 변수 값이 바뀔때 마다 자동으로 break가 걸린다.
continue
또는
c
```
8.2 Watchpoint 나열
```bash
watchpoint list
```
8.2 Watchpoint 삭제
* Watchpoint는 run도중에만 삭제가 가능하다.
```bash
watchpoint delete <ID>
```
9. Process 종료
```bash
kill
```
10. LLDB 종료
```
exit
```