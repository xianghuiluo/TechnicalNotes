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

[Back to Contents](./README.md)
