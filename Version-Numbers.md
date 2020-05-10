# Version Number with CMake

```cmake
cmake_minimum_required(VERSION 3.5)
project(project-name VERSION 4.0)

execute_process(
  COMMAND git rev-parse --short HEAD
  WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}
  OUTPUT_VARIABLE REVISION_NUMBER
  OUTPUT_STRIP_TRAILING_WHITESPACE
)

add_definitions("-DVERSION_MAJOR=${project-name_VERSION_MAJOR}")
add_definitions("-DVERSION_MINOR=${project-name_VERSION_MINOR}")
add_definitions("-DVERSION_BUILD=0x${REVISION_NUMBER}")
```

[Back to Contents](./README.md)
