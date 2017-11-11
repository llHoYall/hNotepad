---
layout: post
title: Control Flow
category: python
tags: python
---

&nbsp;

# Control Flow

### 조건문

##### if

```python
if condition:
    statements
elif condition:
    statements
else:
    statements
```

조건문은 다음과 같이 범위 지정도 간편하게 할 수 있다.

```python
>>> score = 70
>>> if 50 <= score <= 100:
    	grade = "A"
    else:
        grade = "B"
```

다음과 같이 한 줄 조건문도 가능하다.

```python
>>> money = 10
>>> item = "apple" if money > 10 else "banana"
```

조건을 판단할 때, <정수 0, 실수 0.0, 빈 시퀀스 (), [], {}, 빈 문자열 '', None> 은 False로 판단한다.

조건문은 단축 평가 (short circuit evaluation) 된다.

&nbsp;

### 반복문

##### for

```python
for item in sequence:
    statements
```

사용 가능한 시퀀스형 자료는 <문자열, 튜플, 리스트, 딕셔너리, iter()로 생성되는 이터레이터 객체> 등이다.

##### While

```python
while condition:
    statements
```

&nbsp;

### 기타 제어문

##### break

break는 반복문을 종료한다.

##### Continue

continue는 이후 내용을 건너뛰고 다음 반복문을 수행한다.

##### else

else는 반복문과 함께 쓰일 수 있다.

break로 종료되지 않고, 정상적으로 반복문이 종료될 경우에만 수행된다.

##### pass

pass는 아무동작도 수행하지 않음을 명시적으로 나타낼 때 사용한다.

