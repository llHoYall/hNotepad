---
layout: post
title: File
category: python
tags: python
---

&nbsp;

# File

##### Open

파일을 연다.

> *file_object* = **open**(*filename*, *mode*)

- mode : 파일 열기를 할 때 어떤 방식으로 열 것인지를 의미하며, 조합 가능하다.
  - 'r' : 읽기 모드. 생략 시 읽기 모드로 지정된다.
  - 'w' : 쓰기 모드
  - 'a' : 이어쓰기 모드
  - '+' : 읽기+쓰기 모드
  - 't' : 텍스트 모드. 생략 시 텍스트 모드로 지정된다.
  - 'b' : 바이너리 모드

텍스트 모드일 경우, 유닉스에서는 개행 문자가 '\n'으로 적용되고, 윈도우즈에서는 '\r\n'으로 적용된다.

##### Read

파일의 데이터를 읽는다.

> *file_object*.**read**()
>
> *file_object*.**readline**()
>
> *file_object*.**readlines**()

`read()` 함수는 파일의 데이터를 모두 읽는다.

`readline()` 함수는 호출할 때마다 파일에서 한 줄씩 읽는다.

`readlines()` 함수는 파일의 모든 데이터를 라인 단위로 리스트로 읽는다.

##### Write

파일에 데이터를 기록한다.

> *file_object*.**write**(*data*)

`write()` 함수는 몇 바이트를 기록했는지 반환한다.

##### Tell

현재 파일에서 어디까지 읽고 썼는지 위치를 알려준다.

> *file_object*.**tell**()

##### Seek

파일 내에서 사용자가 원하는 위치로 이동한다.

> *file_object*.**seek**(*position*)

- position
  - 0 : 파일의 처음으로 이동한다.

##### Close

파일을 닫는다.

> *file_object*.**close**()

`with` 구문을 사용하면 자동으로 파일을 닫는다.

```python
with open('file.txt') as f:
    f.readlines()
# 파일이 닫혀있는지 확인한다. Boolean 값으로 반환된다.    
print(f.closed)    
```

