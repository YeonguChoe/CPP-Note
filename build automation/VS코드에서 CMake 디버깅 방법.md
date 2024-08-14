# VS코드에서 CMake 디버깅 방법

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "LLDB 디버깅",
            "type": "cppdbg",
            "request": "launch", // 프로그램을 새로 시작하고 디버깅 시작
            "program": "${workspaceFolder}/build/Algorithm",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}/build",
            "environment": [
                {
                    "name": "PATH",
                    "value": "${workspaceFolder}/build:${env:PATH}" // PATH 환경 변수에 build 디렉토리 추가
                },
            ],
            "externalConsole": false,
            "MIMode": "lldb",
            "targetArchitecture": "arm64" // Apple Silicon을 사용함을 명시
        }
    ]
}
```
