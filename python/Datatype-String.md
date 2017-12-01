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

#### Methods

- **capitalize()**
  첫 문자를 대문자로, 나머지 문자를 소문자로 바꿔준다.

- **count(*keyword*[, *start*[, *end*]])**
  포함된 keyword의 개수를 알려준다. 검색범위를 옵션으로 지정할 수 있다.

- **encode([*encoding*[, *errors*]])**
  파이썬3에서 str 클래스는 기본적으로 유니코드이다. 이 메서드를 사용하면 인코딩이 있는 바이너리로 변환된다.

  - errors options
  - **'strict'** : 기본 값. 올바르지 않은 인코딩을 적용하면 UnicodeEncodeError 예외가 발생한다.
  - **'ignore'** : 에러가 난 부분을 무시한다.
  - **'replace'** : 에러가 난 부분을 '?' 등의 문자로 대체한다.
  - **'xmlcharrefreplace'** : 에러가 난 부분을 XML 표현 방식으로 대체한다.
  - **'backslashreplace'** : 에러가 난 부분을 backslash 표현 방식으로 대체한다.

- **endswith(*postfix*[, *start*[, *end*]])**
  postfix로 문자열이 끝나면 True, 그렇지 않다면 False를 반환한다. 범위를 지정할 수 있다.

- **expandtabs([*tabsize*])**
  Tab을 공백으로 치환한다. tabsize 기본 값은 8이다.

- **find(*keyword*[, *start*[, *end*]])**
  문자열에서 keyword가 나타나는 첫 번째 위치를 반환한다. 찾지 못한다면 -1을 반환한다. 범위를 지정할 수 있다.

- **index(*keyword*[, *start*[, *end*]])**
  find() 메서드와 유사하지만 찾지 못할 경우 ValueError 예외가 발생한다.

- **isalnum()**
  문자열이 알파벳과 숫자로만 되어있다면 True, 그렇지 않다면 False를 반환한다.

- **isalpha()**
  문자열이 알파벳으로만 되어있다면 True, 그렇지 않다면 False를 반환한다.

- **islower()**
  문자열의 알파벳이 모두 소문자이면 True, 그렇지 않다면 False를 반환한다.

- **isspace()**
  문자열이 공백 문자(space, tab, newline)로만 되어있다면 True, 그렇지 않다면 False를 반환한다.

- **istitle()**
  문자열이 Title 스타일(모둔 단어의 첫 글자는 대문자, 나머지는 소문자)로 되어있다면 True, 그렇지 않다면 False를 반환한다.

- **isupper()**
  문자열의 알파벳이 모두 대문자이면 True, 그렇지 않다면 False를 반환한다.

- **isdecimal()**, **isdigit()**
  문자열이 10진수로만 되어있다면 True, 그렇지 않다면 False를 반환한다.

- **isnumeric()**
  문자열이 숫자로 되어있다면 True, 그렇지 않다면 False를 반환한다.

- **isidentifier()**
  문자열이 identifier(알파벳이나 '\_'로 시작하고 알파벳, 숫자, '\_'로만 구성)라면 True, 그렇지 않다면 False를 반환한다.

- **isprintable()**
  문자열이 출력 가능한 문자로만 되어있다면 True, 그렇지 않다면 False를 반환한다.

- **join(*sequence*)**
  시퀀스형 변수를 문자열로 연결하여 반환한다.

- **lower()**
  문자열의 모든 알파벳을 소문자로 바꾼다.

- **lstrip([*chars*])**
  문자열의 왼쪽을 잘라낸다. chars를 지정하지 않으면 공백 문자를 제거하며, 지정되어 있을 경우 해당 문자들을 제거한다.

- **maketrans(*x*[, *y*[, *z*]])**
  translate() 메서드에 쓰일 변환용 맵을 반환한다. 인자가 하나일 경우에는 딕셔너리를 입력받고, 두 개일 경우에는 길이가 같은 문자열을 2개를 입력받고, 세 개일 경우에는 길이가 같은 문자열 2개와 None으로 대체될 문자열을 입력받는다.

- **partition(*separator*)**
  문자열을 separator로 나눠 3등분된 튜플을 반환한다.

  ```python
  >>> 'python is powerful'.partition('is')
  ('python ', 'is', ' powerful')     
  ```

- **replace(*old*, *new*[, *count*])**
  문자열에서 old를 new로 교체한 문자열을 반환한다. count 옵션을 사용할 경우 해당 횟수만큼만 교체한다.

- **rfind(*keyword*[, *start*[, *end*]])**
  문자열의 뒤에서부터 keyword가 나타나는 첫 번째 위치를 반환한다. 찾지 못한다면 -1을 반환한다. 범위를 지정할 수 있다.

- **rindex(*keyword*[, *start*[, *end*]])**
  rfind() 메서드와 유사하지만 찾지 못할 경우 ValueError 예외가 발생한다.

- **rpartition(*separator*)**
  문자열을 뒤에서부터 separator로 나눠 3등분된 튜플을 반환한다.

- **rsplit([*separator*[, *maxsplit*]])**
  문자열을 separator로 분리하여 리스트로 반환한다. separator가 생략되면 공백 문자를 구분자로 한다. maxsplit을 지정하면 뒤에서부터 지정한 횟수 만큼만 분리한다.

- **rstrip([*chars*])**
  문자열의 오른쪽을 잘라낸다. chars를 지정하지 않으면 공백 문자를 제거하며, 지정되어 있을 경우 해당 문자들을 제거한다.

- **split([*separator*[, *maxsplit*]])**
  문자열을 separator로 분리하여 리스트로 반환한다. separator가 생략되면 공백 문자를 구분자로 한다. maxsplit을 지정하면 앞에서부터 지정한 횟수 만큼만 분리한다.

- **splitlines([*keep*])**
  여러 라인으로 되어있는 문자열을 분리한다. keep을 True로 설정하면 구분자를 분리된 문자열에서 제거하지 않으며, 기본값인 False로 설정하면 제거한다.

- **startswith(*prefix*[, *start*[, *end*]])**
  prefix로 문자열이 시작하면 True, 그렇지 않다면 False를 반환한다. 범위를 지정할 수 있다.

- **strip([*chars*])**
  문자열의 양쪽 끝을 잘라낸다. chars를 지정하지 않으면 공백 문자를 제거하며, 지정되어 있을 경우 해당 문자들을 제거한다.

- **swapcase()**
  문자열 중 영문자에 대해서 소문자는 대문자로, 대문자는 소문자로변환해서 반환한다.

- **title()**
  문자열의 모든 단어에 대해서 첫 문자는 대문자, 나머지는 소문자로 변환하여 반환한다.

- **upper()**
  문자열의 모든 알파벳을 대문자로 바꾼다.

