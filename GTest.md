# Unit Tests with Google Test

## Install GTest on Ubuntu 20.04
```bash
$ sudo apt install libgtest-dev
$ cd /usr/src/googletest/googletest
$ sudo mkdir build
$ cd build
$ sudo cmake ..
$ sudo make
$ cd lib
$ sudo cp libgtest* /usr/lib/
```
Installation on other versions of Ubuntu are mostly the same.


## Unit Test Example
Create a folder "myproject" and create in the folder the following three files:
* CMakeLists.txt
```cmake
cmake_minimum_required(VERSION 3.0)
project(GTestExample VERSION 1.0)


# Locate GTest
find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS})


# Link runTests with what we want to test and the GTest and pthread library
add_executable(runTests main.cpp sqrt_tests.cpp fabs_tests.cpp)
target_link_libraries(runTests ${GTEST_LIBRARIES} pthread)
```
* main.cpp
* sqrt_tests.cpp
* fabs_tests.cpp

[Back to Contents](./README.md)
