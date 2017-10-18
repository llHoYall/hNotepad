---
layout: post
title: Getting Started
category: swift
tags: swift
---

&nbsp;

# Getting Starte

### Installation

MAC OS X에서는 바로 사용할 수 있다.

&nbsp;

### Run

1. **REPL**

   >  $ swift

   스위프트를 실행시키면 기본적으로 repl 모드로 실행이 된다.

   종료를 하고 싶다면 *:exit*, *:q[uit]* 를 repl에 입력하면 된다.

2. **단일 파일 실행**

   > $ chmod +x program.swift
   > $ ./program.swift

   파일에 실행권한을 주고 바로 실행할 수 있다.

3. **컴파일 후 실행**

   > $ swiftc file1.swift file2.swift -o output
   > $ ./output

   파일들을 묶어 컴파일 후 실행할 수 있다.

&nbsp;

### Terminal Output

```swift
public func print(items: Any..., separator: String = default, terminator: String = default)
```

자동으로 줄바꿈 문자가 삽입된다.

dump() 함수를 사용하면 좀 더 자세한 디버깅 정보를 출력할 수 있다.

```swift
// String
print("Hello World!")

// String Interpolation
let name: String = "HoYa"
print("My name is \(name)")
```

&nbsp;

### Comment

```swift
// One-Line Comment

/*
Multi-Line Comments
*/

/* Nested Comments
/* Comment
// Comment
*/ Comment
*/
```

Markup 문법으로 주석을 작성하면 Quick Help를 통해 확인할 수 있다.

Quick Help는 \<Option> 키를 누른 상태로 원하는 항목을 클릭하거나, 원하는 항목에 커서를 놓은 상태로 \<CMD>+\<OPTION>+2를 눌러 확인할 수 있다.

```swift
/// Markup Comments for Quick Help
/// - item : description

/** Markup COmments for Quick Help
description

- item1
+ item2
* item3

1. item1
2. item2
3. item3

----

*italic*
__bold__
[link](https://blahblah)

# Header1
Header1
===

## Header2
Header2
---

​````
code block
​````

- note
- author
- warning

> information
- parameters:
	- param1: description
	- param2: description
- returns: description
*/
```

