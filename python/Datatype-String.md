---
layout: post
title: Datatype String
category: python
tags: python
---

&nbsp;

# Datatype - String

문자열은 single quotation marks나 double quotation marks로 감싼다.

일반적으로 문자열 내에서 사용할 수 있는 특수 문자는 다음과 같다.

- \n : newline
- \t : tab
- \r : carriage return
- \0 : null
- \\\ : backslash
- \' : single quotation marks
- \" : double quotation marks

따옴표를 3개 사용한 ''', """ 기호를 사용하면 여러 문자열을 사용할 수 있다. 특수문자를 사용하지 않아도 공백이나 탭은 입력한 대로 적용이 된다.

```python
>>> print('''
... Test
...     String
...   Melong
... ''')

Test
        String
  Melong

```

'Test' 위쪽과 'Melong' 아래쪽에 newline이 적용된 것이 보이며, 'String'의 앞은 tab, 'Melong' 앞은 2 space가 각각 적용된 것을 볼 수 있다.

문자열 앞에 r 기호를 붙이면 raw 문자열로 인식되어서 escape 문자가 적용되지 않는다.

```python
>>> print(r'\tTAB\nNEWLINE')
\tTAB\nNEWLINE
```

#### Indexing

문자열은 리스트처럼 인식되어 인덱싱을 할 수 있다. 리스트는 아니다.

```python
>>> a = "Python"
>>> a[0]
'P'
>>> a[3]
'h'
>>> a[0] = 'C'
TypeError: 'str' object does not support item assignment
```

#### Slicing

문자열의 특정 부분을 취할 수 있다. [start : end : step]와 같은 형태로 사용한다.

```python
#  +---+---+---+---+---+---+
#  | P | y | t | h | o | n |
#  +---+---+---+---+---+---+
#  0   1   2   3   4   5   6
# -6  -5  -4  -3  -2  -1
>>> a = "Python"
>>> a[0:1]
'P'
>>> a[2:4]
'th'
>>> a[2:]
'thon'
>>> a[:2]
'Py'
>>> a[-2:]
'on'
>>> a[:-2]
'Pyth'
>>> a[:]
'Python'
>>> a[::2]
'Pto'
```

#### Type Casting

숫자를 문자열로 변환하거나 문자열을 숫자로 변환하려면 자료형 클래스의 생성자를 사용한다.

단, 변환할 수 없는 숫자 혹은 문자가 사용되면 에러가 발생한다.

```python
>>> str(3.14)
'3.14'
>>> int('33')
33
>>> float('6.25')
6.25
```

#### Unicode

현재 시스템의 인코딩은 다음 함수로 알 수 있다.

```python
import sys
sys.stdin.encoding
sys.stdout.encoding
```

어떤 문자의 유니코드 값을 알고 싶거나 유니코드의 값을 문자로 변환할 때는 다음 함수를 사용한다.

```python
>>> ord('s')
115
>>> chr(112)
'p'
```

#### Alignment

```python
# 우측 정렬
>>> 'right'.rjust(10)
'     right'
>>> 'right'.rjust(3)
'right'
# 좌측 정렬
>>> 'left'.ljust(10)
'left      '
# 가운데 정렬
>>> 'center'.center(10)
'  center  '
# 우측 정렬 및 0으로 공백 채우기
>>> 'right'.zfill(10)
'00000right'
```

