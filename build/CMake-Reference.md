---
layout: post
title: CMake - Reference
category: build
tags: [build, cmake]
---



# CMake - Reference

#### cmake_minimum_required

실행하기 위한 cmake의 최소 버전을 명시한다. 반드시 포함되어야 한다.

```cmake
cmake_minimum_required(VERSION major.minor[.patch[.tweak]]
                       [FATAL_ERROR])
```

#### set

변수를 설정한다.

```cmake
# Set Normal Variable
set(<variable> <value>... [PARENT_SCOPE])
# Set Cache Entry
set(<variable> <value>... CACHE <type> <docstring> [FORCE])
# Set Environment Variable
set(ENV{<variable>} <value>...)
```

#### include_directories

빌드에 포함될 디렉토리를 지정한다.

```cmake
include_directories([AFTER|BEFORE] [SYSTEM] dir1 [dir2 ...])
```

#### add_executable

프로젝트의 실행파일을 만들 소스 파일을 명시한다.

```cmake
add_executable(<name> [WIN32] [MACOSX_BUNDLE]
               [EXCLUDE_FROM_ALL]
               [source1] [source2 ...])
```

#### target_link_libraries

타겟에 링크할 라이브러리를 명시한다.

```cmake
# Libraries for a Target and/or its Dependents
target_link_libraries(<target>
                      <PRIVATE|PUBLIC|INTERFACE> <item>...
                     [<PRIVATE|PUBLIC|INTERFACE> <item>...]...)
# Libraries for both a Target and its Dependents                     
target_link_libraries(<target> <item>...)
# Libraries for a Target and/or its Dependents (Legacy)
target_link_libraries(<target>
                      <LINK_PRIVATE|LINK_PUBLIC> <lib>...
                     [<LINK_PRIVATE|LINK_PUBLIC> <lib>...]...)
# Libraries for Dependents Only (Legacy)
target_link_libraries(<target> LINK_INTERFACE_LIBRARIES <item>...)
```

#### message

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

#### add_custom_target

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

#### add_custom_command

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

