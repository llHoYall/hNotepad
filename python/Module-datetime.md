---
layout: post
title: Module - datetime
category: python
tags: python
---

&nbsp;

# Module - datetime

## Date Class

#### Methods

- **date(*year*, *month*, *day*)** : 년, 월, 일로 표기되는 그레고리안 달력의 날짜를 표현한다. 잘못된 날짜를 입력하면 ValueError 예외가 발생한다.
- **fromtimestamp(*timestamp*)** : 타임스탬프 값을 인자로 받아 date 객체를 반환한다.
- **fromordinal(*ordinal*)** : 1년 1월 1일 이후로 누적된 날짜로부터 date 객체를 반환한다.
- **today()** : 현재 시스템의 오늘 날짜의 date 객체를 반환한다.
- **replace(*year*, *month*, *day*)** : 입력된 인자로 변경된 date 객체를 반환한다. 원본 객체는 변경되지 않는다.
- **timetuple()** : date 객체의 값을 time.struct_time 시퀀스 객체에 할당한다. 해당되는 정보가 없는 시, 분, 초는 0으로 초기화된다.
- **toordinal()** : 1년 1월 1일 이후로 date 객체까지 누적된 날짜를 반환한다.
- **weekday()** : 요일을 정수로 변환해 반환한다. (0: 월요일, 6: 일요일)
- **isoformat()** : date 객체의 정보를 'YYYY-MM-DD' 형태의 문자열로 반환한다.
- **ctime()** : date 객체의 정보를 'Tue Dec 05 00:00:00 2017' 형태의 문자열로 반환한다. 시, 분, 초에 대한 정보는 0으로 초기화 된다.
- **strftime(*format*)** : 지정된 형식에 맞춰 date 객체의 정보를 문자열로 반환한다.

#### Attributes

- **year** : 년. (Read only)
- **month** : 월. (Read only)
- **day** : 일. (Read only)
- **max** : date 객체의 최대값. (9999년 12월 31일)
- **min** : date 객체의 최소값. (1년 1월 1일)

&nbsp;

## Time Class

#### Methods

- **time(*hour*[, *minute*[, *second*[, *microsecond*, *tzinfo*]]])** : 시간 정보를 입력받아 time 객체를 생성한다. 잘못된 시간을 입력하면 ValueError 예외가 발생한다.
- **replace([*hour*[, *minute*[, *second*[, *microsecond*[, *tzinfo*]]]]])** : 입력된 값으로 수정된 time 객체를 반환한다. 원본 객체는 변경되지 않는다.
- **isoformat()** : time 객체의 값을 'HH:MM:SS:mmmmmm' 형식이나 'HH:MM:SS' 형식의 문자열을 반환한다.
- **strftime(*format*)** : 지정된 형식에 맞춰 time 객체의 정보를 문자열로 반환한다.

#### Attributes

- **hour** : 시. (Read only)
- **minute** : 분. (Read only)
- **second** : 초. (Read only)
- **microsecond** : 마이크로초. (Read only)
- **max** : time 객체의 최대값. (time(23, 59, 59, 999999))
- **min** : time 객체의 최소값. (time(0, 0, 0, 0))

&nbsp;

## Datetime Class

#### Methods

- **datetime(*year*, *month*, *day*[, *hour*[, *minute*[, *second*[, *microsecond*[, *tzinfo*]]]]])** : 날짜 정보를 입력받아 datetime 객체를 생성한다. 생략한 인자는 0으로 초기화 된다. 잘못된 정보를 입력하면 ValueError 예외가 발생한다.
- **today()** : 현재 시스템 기준의 datetime 객체를 반환한다.
- **now([*tz*])** : 현재 시스템 기준의 datetime 객체를 반환한다. 인자를 입력하면 인자값을 기준으로 한다.
- **utcnow()** : UTC 기준의 datetime 객체를 생성한다.
- **fromtimestamp(*timestamp*[, *tz*])** : 타임스탬프를 LST 기준의 datetime 객체를 반환한다.
- **utcfromtimestamp(*timestamp*)** : 타임스탬프를 UTC 기준의 datetime 객체를 반환한다.
- **fromordinal(*ordinal*)** : 1년 1월 1일 이후로 누적된 날짜로부터 datetime 객체를 반환한다. 시간값은 0으로 할당된다.
- **combine(*date*, *time*)** : date 객체와 time 객체를 입력받아 datetime 객체를 생성한다.
- **strptime(*date_string*, *format*)** : 지정된 형식에 맞는 시간 표현 문자열을 입력받아 datetime 객체를 반환한다.
- **date()** : 원본 객체의 년, 월, 일 정보를 가지고 있는 datetime 객체를 반환한다.
- **time()** : 원본 객체의 시, 분, 초, 마이크로초를 가지고 있는 time 객체를 반환한다.
- **replace()** : 입력된 값으로 변경된 datetime 객체를 반환한다. 원본 객체는 변경되지 않는다.
- **timetuple()** : datetime 객체의 값을 time.struct_time 형식의 시퀀스 객체로 변환해 반환한다.
- **weekday()** : 각 요일을 숫자로 나타낸다. (0: 월요일, 6: 일요일)
- **isoweekday()** : ISO 형식에 맞도록 각 요일을 숫자로 나타낸다. (1: 월요일, 7: 일요일)
- **isocalendar()** : ISO 형식에 맞는 날짜 표현을 튜플로 반환한다. (ISO year, ISO week number, ISO weekday)
- **isoformat()** : datetime 객체를 'YYYY-MM-DDTHH:MM:SS.mmmmmm' 형식이나 'YYYY-MM-DDTHH:MM:SS' 형식으로 변환해 문자열을 반환한다.
- **ctime()** : datetime 객체를 'Fri Dec 08 22:02:03 2017' 형식의 문자열로 반환한다.
- **strftime(*format*)** : 지정된 형식에 맞춰 datetime 객체를 문자열로 반환한다.

#### Attributes

- **year** : 년. (Read only)
- **month** : 월. (Read only)
- **day** : 일. (Read only)
- **hour** : 시. (Read only)
- **minute** : 분. (Read only)
- **second** : 초. (Read only)
- **microsecond** : 마이크로초. (Read only)
- **max** : datetime 객체의 최대값. (datetime(9999, 12, 31, 23, 59, 59, 999999))
- **min** : datetime 객체의 최소값. (datetime(1, 1, 1))

&nbsp;

## Timedelta Class

두 날짜 혹은 시간 사이의 기간을 표현하는 클래스이다.

#### Methods

- **timedelta([*days*[, *seconds*[, *microseconds*[, *milliseconds*[, *minutes*[, *hours*[, *weeks*]]]]]]])** : 생성자 메서드이다. 인자가 양수인 경우 현 시점부터 미래, 음수인 경우 현 시점부터 과거를 나타낸다.

```python
from datetime import timedelta
td1 = timedelta(hours=7)		# 7시간 이후
td2 = timedelta(days=-3)		# 3일 이전
print(td1 + td2)
print(td1 - td2)
print(td1 * 4)
print(td1 // 3)
print(abs(td2))
print(td1 > td2)
```

```python
from datetime import date, timedelta
d = date.today()
td = timedelta(days=3)
print(d + td)
print(d - td)
d2 = d.replace(day=20)
dt = d - d2
print(dt)
print(d2 > d)
```

```python
from datetime import datetime, timedelta
dt = datetime.today()
td = timedelta(days=2, hours=2)
print(dt + td)
print(dt - td)
dt2 = dt.replace(month=1, day=4, hour=7)
print(dt - dt2)
print(dt > dt2)
```

