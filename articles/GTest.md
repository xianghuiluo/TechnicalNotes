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


add_executable(runTests main.cpp sqrt_tests.cpp fabs_tests.cpp)
# Link runTests with what we want to test and the GTest and pthread library
target_link_libraries(runTests ${GTEST_LIBRARIES} pthread)
```
* main.cpp
```C++
#include "gtest/gtest.h"


int main(int argc, char **argv)
{
    ::testing::InitGoogleTest(&argc, argv);
    return RUN_ALL_TESTS();
}
```
* sqrt_tests.cpp
```C++
#include "gtest/gtest.h"
#include <cmath>


TEST(SquareRootTests, PositiveNos)
{
    ASSERT_EQ (std::sqrt (324.0), 18);
    EXPECT_EQ (std::sqrt (625.0), 25);
    ASSERT_NEAR (std::sqrt (2), 1.414, 0.001);
}
```
* fabs_tests.cpp
```C++
#include "gtest/gtest.h"
#include <cmath>


TEST (FabsTests, Zero)
{ 
    ASSERT_EQ (fabs(0.0), 0.0);
}

TEST (FabsTests, Negative)
{
    ASSERT_EQ (fabs(-1), 1);
}
```
To build and run the tests, go to the folder in a terminal and launch the following commands:
```bash
$ mkdir build
$ cd build
$ cmake ..
$ make
$ ./runTests
```
For more information on GTest, here is a good [tutorial](../data/GTest-Framework.pdf).

[Back to Contents](../README.md)
