# VS코드에서 CMake 디버깅 방법

## CMake Tools 디버거 설정 방법
settings.json에서
```json
{
    "workbench.colorTheme": "Visual Studio Light - C++",
    "workbench.startupEditor": "none",
    "cmake.pinnedCommands": [
        "workbench.action.tasks.configureTaskRunner",
        "workbench.action.tasks.runTask"
    ],

    "cmake.debugConfig": {
        // Machine Interface: 디버거와 code editor간의 통신 규약 (프로토콜)
        "MIMode": "lldb", // 디버거를 LLDB로 설정
    }
}
```

## 일반적으로 VS코드에서 디버거 설정 방법
.vscode/launch.json 에서
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
