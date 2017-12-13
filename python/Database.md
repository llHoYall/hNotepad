---
layout: post
title: Database
category: python
tags: python
---

&nbsp;

# Database

파이썬에는 기본적으로 SQLite3 모듈이 내장되어 있다.

#### Functions

- **connect(*database*[, *timeout*, *isolation_level*, *detect_types*, *factory*])** : SQLite3 DB에 연결하고 연결된 Connection 객체를 반환한다.
- **complete_statement(*sql*)** : 세미콜론으로 끝나는 SQL문에 대해 True를 반환한다. 단지 세미콜론으로 끝나는 지만 검사하고, SQL 구문이 올바른지는 검사하지 않는다.
- **register_adapter(*type*, *callable*)** : 사용자정의 파이썬 자료형을 SQLite3에서 사용하도록 등록한다. callable은 이러한 변환을 수행하는 함수로 1개의 인자를 받아 파이썬에서 처리 가능한 자료형으로 변환한다.
- **register_converter(*typename*, *callable*)** : SQLite3에 저장된 자료를 사용자정의 자료형으로 변환하는 함수를 등록한다. typename은 SQLite3에서 내부적으로 사용될 자료형의 이름이고, callable은 변환을 위해 사용되는 함수이다.

## Connection Class

#### Methods

- **cursor()** : Cursor 객체를 생성한다.
- **commit()** : 현재 트랜잭션의 변경 내역을 DB에 반영한다. (commit)
- **rollback()** : 가장 최근의 commit() 이후 지금까지 작업한 내용에 대해 DB에 반영하지 않고 트랜잭션 이전 상태로 되돌린다.
- **close()** : DB 연결을 종료한다. 종료 이전에 commit()이나 rollback()을 호출해야 한다.
- **execute(*sql*[, *parameters*])** : 임시 Cursor 객체를 생성해 해당 execute 계열 메서드를 수행한다.
- **executemany(*sql*[, *parameters*])** : 임시 Cursor 객체를 생성해 해당 execute 계열 메서드를 수행한다.
- **executescript(*sql_script*)** : 임시 Cursor 객체를 생성해 해당 execute 계열 메서드를 수행한다.
- **create_aggregate(*name*, *num_params*, *aggregate_class*)** : 사용자정의 집계 (aggregate) 함수를 생성한다.
- **create_callation(*name*, *callable*)** : 문자열 정렬 시 SQL 구문에서 사용될 이름과 정렬 함수를 지정한다. callable 함수는 인자로 문자열 2개를 받으며, 첫 번쨰 문자열이 두 번째 문자열보다 순서가 낮은 경우 -1, 같은 경우 0, 높은 경우 1을 반환해야 한다.
- **iterdump()** : 연결된 DB의 내용을 SQL 질의 형태로 출력할 수 있는 이너레이터를 반환한다.

#### Attributes

- **isolation_level** : 트랜잭션의 격리 수준을 확인/설정한다.
  - None
  - DEFERRED
  - IMMEDIATE
  - EXCLUSIVE

## Cursor Class

데이터베이스에 SQL 문장을 수행하고, 조회된 결과를 가져오는 클래스이다.

#### Methods

- **execute(*sql*[, *parameters*])** : SQL 문장을 실행한다.
- **executemany(*sql*, *seq_of_parameters*)** : 동일한 SQL 문장을 매개변수만 변경하면서 수행한다.
- **executescript(*sql_script*)** : 세미콜론으로 구분된 연속된 SQL 문장을 수행한다.
- **fetchone()** : Record set으로부터 데이터 1개를 반환한다. 데이터가 없는 경우 None을 반환한다.
- **fetchmany([size=cursor.arraysize])** : 결과로부터 입력받은 size 만큼의 데이터를 리스트 형태로 반환한다. 데이터가 없는 경우 빈 리스트를 반환한다.
- **fetchall()** : 결과 모두를 리스트 형태로 반환한다. 데이터가 없는 경우 빈 리스트를 반환한다.

## Row Class

Result set에서 Row 객체는 관계형 데이터베이스 모델에서 튜플을 나타낸다. 예를 들어 JOIN 연산을 이용해 2개 이상의 테이블을 조회한 결과인 경우, Row 객체는 결과 뷰의 한 행을 나타낸다.

&nbsp;

```python
import sqlite3

# DB Connection
conn = sqlite3.connect("test.db")	# Make file to storage
conn = sqlite3.connect(":memory:")	# Make file to memory
# 메모리에 저장하면 연결 종료 시 작업 내용이 사라지지만 연산 속도가 빠르다.

# SQL Execution
cur = conn.cursor()
cur.execute("CREATE TABLE PhoneBook(Name text, PhoneNum text);")
cur.execute("INSERT INTO PhoneBook VALUES('HoYa', '012-3456-7890');")

name = 'HoYa'
phoneNumber = '012-3456-7890'
cur.execute('INSERT INTO PhoneBook VALUES(?, ?);', (name, phoneNumber))
cur.execute('INSERT INTO PhoneBook VALUES(:inputName, :inputNum);', {'inputNum': phoneNumber, 'inputName': name})

datalist = (('kim', '010-2222-3333'), ('lee', '010-4444-5555'))
cur.executemany('INSERT INTO PhoneBook VALUES(?, ?);', datalist)

def dataGenerator():
    datalist = {('kim', '010-2222-3333'), ('lee', '010-4444-5555')}
    for item in datalist:
        yield item
cur.executemany('INSERT INTO PhoneBook VALUES(?, ?);', dataGenerator())   

with open('script.txt') as f:
    SQLScript = f.read()
cur.executescript(SQLScript)

# Record Fetch
cur.execute('SELECT * FROM PhoneBook;')
for row in cur:
    print(row)
cur.execute('SELECT * FROM PhoneBook;')
cur.fetchone()
cur.fetchmany(2)
cur.fetchall()
```

