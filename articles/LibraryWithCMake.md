# Library Building and Usage with CMake

## Building and Installing a Library
* CMakeLists.txt
```cmake
set(MY_INCLUDE_DESTINATION ~/MyLibraries/include)
set(MY_LIB_DESTINATION ~/MyLibraries/lib)
set(MY_BIN_DESTINATION ~/MyLibraries/bin)
.
.
.
.
.
.
install(TARGETS 
  <lib-name>
  ARCHIVE DESTINATION ${MY_LIB_DESTINATION}
  LIBRARY DESTINATION ${MY_LIB_DESTINATION}
  RUNTIME DESTINATION ${MY_BIN_DESTINATION}/${PROJECT_NAME}
)

file(GLOB headers "*.h" "*.hpp")
install(FILES ${headers}
  DESTINATION ${MY_INCLUDE_DESTINATION}/${PROJECT_NAME}
)
```

[Back to Contents](../README.md)
