# Version Number with CMake

This note will go through an example of using version numbers in C++ programs with CMake.

```cmake
cmake_minimum_required(VERSION 3.5)
project(project-name VERSION 4.0)

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
```

[Back to Contents](./README.md)
