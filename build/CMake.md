---
layout: post
title: CMake
category: build
tags: [build, cmake]
---

&nbsp;

# CMake

CMake를 사용하는 방법이다.

&nbsp;

## Example

> |- **CMakeLists.txt**
>
> |- src
>
> |   |- **CmakeLists.txt**
>
> |   |- **main.c** ​
>
> |   \+- sub
>
> |         |- **CMakeLists.txt**
>
> |         \+- **sub.c**
>
> |- inc
>
> |   \+ sub
>
> |         \+- **sub.h**
>
> \+- cmake

```cmake
# CMakeLists.txt
cmake_minimum_required (VERSION 3.5)

set (CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set (CMAKE_C_COMPILER "/usr/bin/clang")
set (CMAKE_CXX_COMPILER "/usr/bin/clang++")
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

&nbsp;

## References

##### cmake_minimum_required

실행하기 위한 cmake의 최소 버전을 명시한다. 반드시 포함되어야 한다.

```cmake
cmake_minimum_required (VERSION 3.5)
```

##### set

변수를 설정한다.

```cmake
# 실행 파일을 빌드 디렉토리 최상단으로 옮겨준다.
set (CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
```

##### message

메세지를 터미널에 출력할 때 사용한다.

```cmake
# message ([<mode>] "message to display...")
# mode
# - STATUS : incidental information
# - WARNING : CMake Warning, continue processing
# - SEND_ERROR : CMake Error, continue processing
# - FATAL_ERROR : CMake Error, stop processing and generation

message(STATUS "Test: " ${TEST})
```

##### add_custom_target

```cmake
# add_custom_target (
#	Name [ALL] [command1 [args1 ...]]
#	[COMMAND command2 [args2 ...] ...]
#	[DEPENDS depend ...]
#	[BYPRODUCTS [files ...]]
#	[WORKING_DIRECTORY dir]
#	[COMMENT comment]
#	[VERBATIM]
#	[USES_TERMINAL]
#	[COMMAND_EXPAND_LISTS]
#	[SOURCES src1 [src2 ...]]
# )
```

##### add_custom_command

```cmake
# add_custom_command ()
#	OUTPUT output1 [output2 ...]
#	COMMAND command1 [ARGS] [args1 ...]
#	COMMAND2 command2 [ARGS] [args2 ...] ...]
#	[MAIN_DEPENDENCY depend]
#	[DEPENDS [depends ...]]
#	[BYPRODUCTS [files ...]]
#	[IMPLICIT_DEPENDS Mlang1> depend1 [<lang2> depends] ...]
#	[WORKING_DIRECTORY dir]
#	[COMMENT comment]
#	[DEPFILE depfile]
#	[VERBATIM]
#	[APPEND]
#	[USES_TERMINAL]
#	[COMMAND_EXPAND_LISTS]
# )
```

