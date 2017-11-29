---
layout: post
title: Module - ctypes
category: python
tags: python
---

&nbsp;

# Module - ctypes

ctypes 모듈은 C의 데이터 타입이나 DLL 혹은 shared library의 함수를 직접 사용할 수 있다.

```python
>>> import ctypes

# 'stdcall' 방식의 함수. 불려진 함수가 스택에서 인자를 꺼내는 방식.
>>> print(ctypes.windll.kernel32)
<WinDLL 'kernel32', handle ... at ...>

# 'cdecl' 방식의 함수. 호출한 함수에서 스택의 인자를 꺼내는 방식.
>>> print(ctypes.cdll.msvcrt)
<CDLL 'msvcrt', handle ... at ...>
```

```python
from ctypes import *

# integer
i = c_int(10)
print(i, i.value)

# pointer
p = pointer(i)
print(pointer(i), p.contents)

# structure / union
class POINT(ctypes.Structure):
    _fields_ = [("x", ctypes.c_int), ("y", ctypes.c_int)]
point = POINT(10, 20)
print(point.x, point.y)		# 10, 20
point = POINT(y=5)
print(point.x, point.y)		# 0, 5
```

구조체나 유니온은 파이썬에서 class로 표현되기 때문에 class 객체를 생성하고 \_fields\_ 멤버 변수를 이용해 각 멤버 변수를 설정해준다.

&nbsp;

### Example

윈도우의 MessageBoxA() 함수를 ctypes 모듈을 사용하여 호출해보자.

```C
// defined in <winuser.h>
WINUSERAPI int WINAPI MessageBoxA(
  HWND hWnd,
  LPCSTR lpText,
  LPCSTR lpCaption,
  UINT uType
);
```

위와 같이 정의된 함수를 ctypes 모듈로 wrapping하여 사용해보자.

```python
from ctypes import c_int, WINFUNCTYPE, windll
from ctypes.wintypes import HWND, LPCWSTR, UINT

prototype = WINFUNCTYPE(c_int, HWND, LPCWSTR, LPCWSTR, UINT)
paramflags = (1, "hwnd", 0), (1, "text", "Hi"), (1, "caption", None), (1, "flags", 0)
MessageBox = prototype(("MessageBoxA", windll.user32), paramflags)

MessageBox(text="Hello World")
MessageBox(text="Hi?", flags=3)
```

이번엔 직접 호출하여 사용해보자.

```python
MB_OK = 0x00
ctypes.windll.user32.MessageBoxA(0, "Hello World".encode('utf8'), 'Title'.encode('utf8'), MB_OK)
```

&nbsp;

### Reference

| ctypes       | C                                      | Python          |
| ------------ | -------------------------------------- | --------------- |
| c_short      | short                                  | int             |
| c_ushort     | unsigned short                         | int             |
| c_int        | int                                    | int             |
| c_uint       | unsigned int                           | int             |
| c_long       | long                                   | int             |
| c_ulong      | unsigned long                          | int             |
| c_longlong   | __int64 or long long                   | int             |
| c_ulonglong  | unsigned __int64 or unsigned long long | int             |
| c_float      | float                                  | float           |
| c_double     | double                                 | float           |
| c_longdouble | long double                            | float           |
| c_char_p     | char* (NULL terminated)                | unicode or None |
| c_wchar_p    | wchar_t* (NULL terminated)             | unicode or None |

