---
layout: post
title: CMake - Reference
category: devtools
tags: [devtools, cmake]
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

#### project

프로젝트 설정을 한다.

```cmake
project(<PROJECT-NAME> [LANGUAGES] [<language-name>...])
project(<PROJECT-NAME>
        [VERSION <major>[.<minor>[.<patch>[.<tweak>]]]]
        [DESCRIPTION <project-description-string>]
        [LANGUAGES <language-name>...])
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

#### target_include_directories

타겟에 포함될 디렉토리를 지정한다.

```cmake
target_include_directories(<target> [SYSTEM] [BEFORE]
                           <INTERFACE|PUBLIC|PRIVATE> [items1...]
                          [<INTERFACE|PUBLIC|PRIVATE> [items2...] ...])
```

#### target_compile_definitions

타겟에 컴파일 definition을 지정한다.

```cmake
target_compile_definitions(<target>
                           <INTERFACE|PUBLIC|PRIVATE> [items1...]
                          [<INTERFACE|PUBLIC|PRIVATE> [items2...] ...])
```

#### set_target_properties

빌드에 포함될 properties를 지정한다.

```cmake
set_target_properties(target1 target2 ...
                      PROPERTIES prop1 value1
                      prop2 value2 ...)
```

##### Properties on Targets

- `COMPILE_FLAGS`
- `LINK_FLAGS`
- `LINK_FLAGS_<CONFIG>` : `LINK_FLAGS_DEBUG`, `LINK_FLAGS_RELEASE`, ...

#### message

메세지를 터미널에 출력할 때 사용한다.

```cmake
message([<mode>] "message to display" ...)
```

##### \<mode>

- (none) : Important information
- `STATUS` : Incidental information
- `WARNING` : CMake Warning, continue processing
- `AUTHOR_WARNING` : CMake Warning (dev), continue processing
- `SEND_ERROR` : CMake Error, continue processing, but skip generation
- `FATAL_ERROR` : CMake Error, stop processing and generation
- `DEPRECATION` : CMake Deprecation Error or Warning if variable CMAKE_ERROR_DEPRECATED or CMAKE_WARN_DEPRECATED is enabled, respectively, else no message.

#### add_custom_target

Output 없는 타겟을 추가한다.

```cmake
add_custom_target(Name [ALL] [command1 [args1...]]
                  [COMMAND command2 [args2...] ...]
                  [DEPENDS depend depend depend ... ]
                  [BYPRODUCTS [files...]]
                  [WORKING_DIRECTORY dir]
                  [COMMENT comment]
                  [VERBATIM] [USES_TERMINAL]
                  [COMMAND_EXPAND_LISTS]
                  [SOURCES src1 [src2...]])
```

#### add_custom_command

Custom 빌드 규칙을 생성된 빌드 시스템에 추가한다.

```cmake
# Generating Files
add_custom_command(OUTPUT output1 [output2 ...]
                   COMMAND command1 [ARGS] [args1...]
                   [COMMAND command2 [ARGS] [args2...] ...]
                   [MAIN_DEPENDENCY depend]
                   [DEPENDS [depends...]]
                   [BYPRODUCTS [files...]]
                   [IMPLICIT_DEPENDS <lang1> depend1
                                    [<lang2> depend2] ...]
                   [WORKING_DIRECTORY dir]
                   [COMMENT comment]
                   [DEPFILE depfile]
                   [VERBATIM] [APPEND] [USES_TERMINAL]
                   [COMMAND_EXPAND_LISTS])
# Build Events
add_custom_command(TARGET <target>
                   PRE_BUILD | PRE_LINK | POST_BUILD
                   COMMAND command1 [ARGS] [args1...]
                   [COMMAND command2 [ARGS] [args2...] ...]
                   [BYPRODUCTS [files...]]
                   [WORKING_DIRECTORY dir]
                   [COMMENT comment]
                   [VERBATIM] [USES_TERMINAL])
```

