### BUILD SYSTEM

It's a tool that makes the management of source code producing a binary
accordingly the specs defined on the build system's config file

### How to use this?

In this text we will cover about `cmake` usage, the cmake config file is
`CMakeLists.txt`

To start with cmake we need first define a cmake version like that

```
# the latest version when this text was writed was the 3.10 version
cmake_minimum_required(VERSION 3.10)
```

after cmake version is defined we will set some variables

```
# we will set this variable to change this only on time in the cmake file specs,
# and reuse this variable when necessary
set(PROJECT "project-name")

# this define the compiler to *.cpp files
set(CMAKE_CXX_COMPILER "unix-path-to-binary")
```

now we can define some metadata about current project 

```
project(
    ${PROJECT}
    VERSION 1.0.0
    DESCRIPTION "project description"
    LANGUAGES CXX
)
```

it's necessary to define how the build system will produce the binary file and
what files will be used to produce the binary

```
add_executable(
    ${PROJECT}
    # here we list all necessaries files in the compilation to program start
    # correctly as expected
    main.cpp
    *.cpp
)
```

and in cmake we have some special function that defines the compiler behavior,
always stating with `target_*` (all target_* function need to be defined after
executable definition inside `add_executable` function)

```
# used to setup the compiler standard
target_compile_features(${PROJECT} PRIVATE cxx_std_20)

# used to setup compiler flags options
target_compile_options(
    ${PROJECT}
    PRIVATE
    -Wall
    -Werror
    -Wextra
    -Weffc++
    -Wsign-conversion
    -Wimplicit-fallthrough
)
```

to finish as basic knowledge, we can produce a cmake config file aggregation
defining another config file inside a project subfolder and compose these files
with the following function

```
add_subdirectory(path-to-sub-directory-to-be-aggregated)
```

to generate the binary we have some methods to do that:

- default usage

```
$ mkdir build
$ cd build
$ cmake ..
$ make
```

- using ninja

```
$ mkdir build
$ cd build
$ cmake -G Ninja ..
$ ninja
```

### Related resources

- ninja build
- autotools
- make
- Makefile

by @thebe111

