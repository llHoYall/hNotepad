---
layout: post
title: CMake - Usage
category: build
tags: [build, cmake]
---



# CMake - Usage

CMake를 사용하는 방법이다.



## Example

```cmake
# Project Structure
###########################
# +- CMakeLists.txt
# +- [src]
# |   +- CmakeLists.txt
# |   +- main.c 
# |   +- [sub]
# |       +- CMakeLists.txt
# |       +- sub.c
# +- [inc]
#     + [sub]
#         +- sub.h
###########################
```

```cmake
# CMakeLists.txt

# 실행하기 위한 cmake의 최소 버전을 명시한다. 반드시 포함되어야 한다.
cmake_minimum_required (VERSION 3.5)

# 실행 파일을 빌드 디렉토리 최상단으로 옮겨준다.
set (CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set (CMAKE_C_COMPILER "/usr/bin/clang")
set (CMAKE_CXX_COMPILER "/usr/bin/clang++")
set (CMKAE_C_FLAGS "-std=gnu11 -Os -Wall -Wextra -Wshadow")
set (CMAKE_CXX_FLAGS "-O2")
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall")
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Werror")
set (CMAKE_BUILD_TYPE Debug)	# Release

project (Test)

add_subdirectory (src)
```

```cmake
# src/CMakeLists.txt
include_directories (../inc/sub)

add_subdirectory (sub)

add_executable (Main main.c)

target_link_libraries (Main Sub)
```

```cmake
# src/sub/CMakeLists.txt
add_library (Sub sub.c)
```


