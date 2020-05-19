# Debug C++ Programs with GDB in VS Code

```
myproject/
    .vscode/
        tasks.json
        launch.json
    CMakeLists.txt
    main.cpp
```
* main.cpp
```C++
#include <iostream>


int main(int argc, char* argv[])
{
    for (int i=0; i < 10; ++i)
    {
        std::cout << "i: " << i << std::endl;
    }
}
```
* CMakeLists.txt
```cmake
cmake_minimum_required(VERSION 3.5)
project(myproject VERSION 1.0)

## Compile as C++11
set (CMAKE_CXX_STANDARD 11)
set (CMAKE_CXX_STANDARD_REQUIRED YES)

	
# Build the executable
add_executable (main main.cpp)
```
* tasks.json
```json
{
    "version": "2.0.0",
    "tasks":
    [
        {
            "type": "shell",
            "label": "cmake",
            "command": "/usr/bin/cmake",
            "args": 
	    [
                "-DCMAKE_BUILD_TYPE=Debug",
                "..",
            ],
            "options": 
	    {
                "cwd": "${workspaceRoot}/build"
            },
            "problemMatcher": 
	    [
                "$gcc"
            ],
            "group": "build"
        },
        {
            "type": "shell",
            "label": "make",
            "command": "/usr/bin/make",
            "args": [],
            "options": 
	    {
                "cwd": "${workspaceRoot}/build"
            },
            "problemMatcher": 
	    [
                "$gcc"
            ],
            "group": "build"
        }
    ]
}
```
* launch.json
```json
{
    "version": "0.2.0",
    "configurations": 
    [
        {
            "name": "(gdb) Launch",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceFolder}/build/a.out",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}/build/",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "setupCommands": 
	    [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ]
        }
    ]
}
```

[Back to Contents](../README.md)
