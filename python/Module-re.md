---
layout: post
title: Module - re
category: python
tags: python
---

&nbsp;

# Module - re

re 모듈은 정규 표현식의 사용을 도와준다.

일반 문자와 특수 문자를 조합하여 정규 표현식의 패턴을 만든다.

자주 사용되는 문자열의 집합이 escape 문자열로 정의되어 있다.

#### Special Character

- **.** : 개행 문자를 제외한 문자 1개. `re.DOTALL`이 설정되어 있으면 개행 문자도 포함한다.
- **^** : 문자열의 시작. `re.MULTILINE`이 설정되어 있으면 모든 라인마다 매칭된다.
- **$** : 문자열의 끝. `re.MULTILINE`이 설정되어 있으면 모든 라인마다 매칭된다.
- **[]** : 문자의 집합. '^'문자가 집합안에 쓰인 경우 제외를 나타낸다. '$'문자가 집합안에 쓰인 경우 해당 문자 자체를 나타낸다.
- **|** : OR
- **()** : 그룹. 해당 문자 자체를 나타내려면 '\\(', '\\)'와 같이 escape 한다.
- ***** : 문자가 0회 이상 반복.
- **+** : 문자가 1회 이상 반복.
- **?** : 문자가 0 또는 1회 반복.
- **{*m*}** : 문자가 m회 반복
- **{*m*, *n*}** : 문자가 m회부터 n회까지 반복.
- **{*m*, }** : 문자가 m회부터 무한 반복.

#### Escape Sequence

- **\\w** : 아스키코드인 경우 [a-zA-Z0-9\_]. 유니코드인 경우 숫자, underline을 포함하는 모든 언어의 표현 가능한 문자.
- **\\W** : 아스키코드인 경우 \[^a-zA-Z0-9_]. 유니코드인 경우 숫자, underline, 표현 가능한 문자를 제외한 나머지 문자.
- **\\d** : 아스키코드인 경우 [0-9]. 유니코드인 경우 [0-9]를 포함하는 모든 숫자.
- **\\D** : 아스키코드인 경우 \[^0-9]. 유니코드인 경우 숫자를 제외한 모든 문자.
- **\\s** : 아스키코드인 경우 [ \t\n\r\f\v]. 유니코드인 경우 [ \t\n\r\f\v]를 포함하는 모든 공백 문자.
- **\\S** : 아스키코드인 경우 \[^ \t\n\r\f\v]. 유니코드인 경우 공백 문자를 제외한 모든 문자.
- **\\b** : 단어의 시작과 끝의 빈 공백.
- **\\B** : 단어의 시작과 끝이 아닌 빈 공백.
- **\\\\** : Backslash.
- **\\[*#*]** : 지정된 숫자만큼 일치하는 문자열.
- **\\A** : 문자열의 시작.
- **\\Z** : 문자열의 끝.

#### Methods

- **re.search(*pattern*, *string*[, *flags*])**
  string에서 pattern을 검색하여 MatchObject 인스턴스를 반환한다. 일치하는 문자열이 없다면 None을 반환한다.

- **re.match(*pattern*, *string*[, *flags*])**
  string의 시작부터 pattern을 검색하여 MatchObject 인스턴스를 반환한다. 즉, 찾고자 하는 내용이 문자열 중간에 있다면 re.search()와 달리 찾지 못한다. 일치하는 문자열이 없다면 None을 반환한다.

- **re.split(*pattern*, *string*[, maxsplit=0])**
  pattern을 구분자로 string을 분리해 리스트로 반환한다.

- **re.findall(*pattern*, *string*[, *flags*])**
  string에서 pattern을 검색하여 리스트로 반환한다.

- **re.finditer(*pattern*, *string*[, *flags*])**
  string에서 pattern을 검색하여 이터레이터 객체로 반환한다.

- **re.sub(*pattern*, *repl*, *string*[, *count*])**
  string에서 pattern을 검색하여 repl로 교체를 하고 결과 문자열을 반환한다.

  ```python
  # 매칭된 문자열을 변경할 문자열에 사용하기.

  # 문자열 앞에 'r'을 붙이면 raw string notation을 뜻한다.
  # repl 부분의 '\1'은 pattern의 결과를 나타낸다.
  re.sub(r"\b(\d{4}-\d{4})\b", r"<I>\1</I>", "Copyright HoYa 1982-2982")
  # 'Copyright HoYa <I>1982-2982</I>

  # '\1'대신 명시적인 이름을 갖도록 할 수 있다.
  # '?P<pattern_name>'으로 패턴에 이름을 붙이고, '\g<pattern_name>'으로 사용한다.
  re.sub(r"\b(?P<year>\d{4}-\d{4})\b", r"<I>\g<year></I>", "Copyright HoYa 1982-2982")
  # 'Copyright HoYa <I>1982-2982</I>
  ```

  ```python
  # 변경할 문자열에 함수를 사용하기.

  def Upper(m):
      return m.group().upper()
  re.sub("[T|t]he", Upper, "The time is the money")
  # 'THE time is THE money'
  ```

- **re.subn(*pattern*, *repl*, *string*[, *count*])**
  re.sub()함수와 유사하지만 결과로 (결과 문자열, 매칭 횟수)를 튜플로 반환한다.

- **re.escape(*string*)**
  영문자, 숫자가 아닌 문자에 대하여 backslash 문자를 추가한다. 메타문자를 포함한 문자열을 정규 표현식으로 변경할 수 있다.

- **re.compile(*pattern*[, *flags*])**
  pattern을 컴파일하여 정규 표현식 객체를 반환한다.

  ```python
  c = re.compile(r"app\w*")
  c.findall("application orange apple banana")
  ```

  - flags
    - **re.I**, **re.IGNORECASE** : 대소문자를 구분하지 않는다.
    - **re.M**, **re.MULTILINE** : 문자열이 여러 라인인 경우 '^'는 각 라인의 시작, '\$'는 각 라인의 끝을 나타낸다. 기본 값은 '^'는 첫 라인의 시작, '\$'는 마지막 라인의 끝을 나타낸다.
    - **re.S**, **re.DOTALL** : 개행 문자도 '.'으로 매칭된다.
    - **re.X**, **re.VERBOSE** : 정규 표현식에서 '#'으로 시작하는 주석과 빈 공백은 무시된다. 빈 공백은 '\ '와 같이 표현한다.
    - **re.A**, **re.ASCII** : '\w', '\W', '\b', '\B', '\s', '\S'가 유니코드 대신 아스키 코드만 매칭된다.
    - **re.L**, **re.LOCALE** : '\w', '\W', '\b', '\B', '\s', '\S'가 현재 locale 설정을 따른다.
  - **search(*string*[, *pos*[, *endpos*]])**
  - **match(*string*[, *pos*[, *endpos*]])**
  - **split(*string*[, maxsplit=0])**
  - **findall(*string*[, *pos*[, *endpos*]])**
  - **finditer(*string*[, *pos*[, *endpos*]])**
  - **sub(*repl*, *string*[, count=0])**
  - **subn(*repl*, *string*[, count=0])**

#### Match Object

매치 객체는 search(), match()의 실행 결과로 반환되며, 결과에 따라 내부적으로 boolean 값을 갖고 있다.

```python
import re

checker = re.compile(r"(\d{2,3})-(\d{3,4})-(\d{4})")
bool(checker.match("01-234-5678"))		# True
m = checker.match("01-234-5678")
m.group()		# '01-234-5678'
m.group(1)		# '02'
m.groups()		# ('01', '234', '5678')
m.start()		# 0
m.start(2)		# 3
m.end()			# 11
m.end(2)		# 6
m.string[m.start(2):m.end(3)]	# '234-5678'
m = re.match(r"(?P<area_code>\d+)-(?P<exchange_number>\d+)-(?P<user_number>\d+)", "01-234-5678")
m.group('user_number')		# '5678'
m.groupdict()				# {'area_code': '01', 'excnage_number': '234', 'user_number': '5678'}
m.start('user_number')		# 7
```

##### Methods

- **group([*group1*, ...])**
  입력받은 인덱스에 해당하는 매칭된 문자열 결과의 부분집합을 반환한다. 인덱스가 0이거나 입력되지 않은 경우 전체 매칭 문자열을 반환한다.
- **groups()**
  매칭된 결과를 튜플로 반환한다.
- **groupdict()**
  이름이 붙여진 매칭 결과를 딕셔너리 형태로 반환한다.
- **start([*group*])**
  매칭된 결과 문자열의 시작 인덱스를 반환한다. 인자로 부분 집합의 번호나 명시된 이름이 전달된 경우, 그에 해당하는 시작 인덱스를 반환한다.
- **end([*group*])**
  매칭된 결과 문자열의 종료 신덱스를 반환한다. 인자로 부분 집합의 번호나 명시된 이름이 전달된 경우, 그에 해당하는 종료 인덱스를 반환한다.

##### Attributes

- **pos** : 원본 문자열에서 검색을 시작하는 위치.
- **endpos** : 원본 문자열에서 검색을 종료하는 위치.
- **lastindex** : 매칭된 결과 집합에서 마지막 인덱스 번호를 반환한다. 일치된 결과가 없는 경우에는 None을 반환한다.
- **lastgroup** : 매칭된 결과 집합에서 마지막으로 일치한 이름을 반환한다. 정규 표현식의 매칭 조건에 이름이 지정되지 않았거나 일치된 결과가 없는 경우에는 None을 반환한다.
- **string** : 매칭의 대상이 되는 원본 문자열.

#### Greedy & Lazy (Non-Greedy)

Greedy 방식은 조건을 만족하는 한 가장 긴 문자열을 선택하는 방식. ".*"

Lazy 방식은 조건을 만족하는 한 가장 짧은 문자열을 선택하는 방식. ".*?"