# Version Number with CMake

This note will go through a minimal example of using version numbers in C++ programs with CMake.

Create a folder "myproject" and create in the folder a file "CMakeLists.txt" with the following content:
```cmake
cmake_minimum_required(VERSION 3.5)
project(project-name VERSION 1.0)

## Compile as C++11
set (CMAKE_CXX_STANDARD 11)
set (CMAKE_CXX_STANDARD_REQUIRED YES)

## Get the commit number and put it in REVISION_NUMBER
execute_process(
  COMMAND git rev-parse --short HEAD
  WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}
  OUTPUT_VARIABLE REVISION_NUMBER
  OUTPUT_STRIP_TRAILING_WHITESPACE
)

## Define three macros: VERSION_MAJOR, VERSION_MINOR, VERSION_BUILD
add_definitions("-DVERSION_MAJOR=${project-name_VERSION_MAJOR}")
add_definitions("-DVERSION_MINOR=${project-name_VERSION_MINOR}")
add_definitions("-DVERSION_BUILD=0x${REVISION_NUMBER}")

## Create an executable
add_executable (myprogram myprogram.cpp)
```
Also create a C++ program "myprogram.cpp" with the following content:
```C++
#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Version Number: "
              << VERSION_MAJOR << "." 
              << VERSION_MINOR << "." << std::hex
              << VERSION_BUILD << std::endl;
}
```
In a terminal, go to the folder and launch the following commands to see the results:
```shell
$ git init
$ git add CMakeLists.txt myprogram.cpp
$ git commit -m "first commit"
$ git log # check the commit number
$ mkdir build
$ cd build
$ cmake ..
$ make
$ ./myprogram # check the output of the program
```


[Back to Contents](./README.md)
