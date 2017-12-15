---
layout: post
title: Database
category: python
tags: python
---

&nbsp;

# Database

파이썬에는 기본적으로 SQLite3 모듈이 내장되어 있다.

#### Datatype

- **NULL** : 파이썬의 None
- **INTEGER** : 파이썬의 int
- **REAL** : 파이썬의 float
- **TEXT** : 파이썬의 str, bytes
- **BLOB** : 바이너리 파일을 데이터베이스에 직접 저장. 파이썬의 buffer

#### Functions

- **connect(*database*[, *timeout*, *isolation_level*, *detect_types*, *factory*])** : SQLite3 DB에 연결하고 연결된 Connection 객체를 반환한다.
- **complete_statement(*sql*)** : 세미콜론으로 끝나는 SQL문에 대해 True를 반환한다. 단지 세미콜론으로 끝나는 지만 검사하고, SQL 구문이 올바른지는 검사하지 않는다.
- **register_adapter(*type*, *callable*)** : 사용자정의 파이썬 자료형을 SQLite3에서 사용하도록 등록한다. callable은 이러한 변환을 수행하는 함수로 1개의 인자를 받아 파이썬에서 처리 가능한 자료형으로 변환한다.
- **register_converter(*typename*, *callable*)** : SQLite3에 저장된 자료를 사용자정의 자료형으로 변환하는 함수를 등록한다. typename은 SQLite3에서 내부적으로 사용될 자료형의 이름이고, callable은 변환을 위해 사용되는 함수이다.
- **abs(*x*)** : 인자의 절대값을 반환한다.
- **length(*x*)** : 인자로 받은 문자열의 길이를 반환한다.
- **lower(*x*)** : 인자로 받은 문자열을 소문자로 반환한다. 원본 문자열은 변화가 없다.
- **upper(*x*)** : 인자로 받은 문자열을 대문자로 반환한다. 원본 문자열은 변화가 없다.
- **min(*x*, *y*, ...)** : 인자 중 가장 작은 값을 반환한다.
- **max(*x*, *y*, ...)** : 인자 중 가장 큰 값을 반환한다.
- **random(*\**)** : 임의의 정수를 반환한다.
- **count(*x*)** : 조회 인자 중 필드 인자가 NULL이 아닌 튜플의 개수를 반환한다.
- **count(*\**)** : 조회 결과의 튜플의 개수를 반환한다.
- **sum(*x*)** : 조회 결과 중 필드 인자의 합을 반환한다.

## Connection Class

#### Methods

- **cursor()** : Cursor 객체를 생성한다.
- **commit()** : 현재 트랜잭션의 변경 내역을 DB에 반영한다. (commit) 트랜잭션은 데이터베이스에서 논리적 작업의 단위이다.
- **rollback()** : 가장 최근의 commit() 이후 지금까지 작업한 내용에 대해 DB에 반영하지 않고 트랜잭션 이전 상태로 되돌린다.
- **close()** : DB 연결을 종료한다. 종료 이전에 commit()이나 rollback()을 호출해야 한다.
- **execute(*sql*[, *parameters*])** : 임시 Cursor 객체를 생성해 해당 execute 계열 메서드를 수행한다.
- **executemany(*sql*[, *parameters*])** : 임시 Cursor 객체를 생성해 해당 execute 계열 메서드를 수행한다.
- **executescript(*sql_script*)** : 임시 Cursor 객체를 생성해 해당 execute 계열 메서드를 수행한다.
- **create_aggregate(*name*, *num_params*, *aggregate_class*)** : 사용자정의 집계 (aggregate) 함수를 생성한다.
- **create_collation(*name*, *callable*)** : 문자열 정렬 시 SQL 구문에서 사용될 이름과 정렬 함수를 지정한다. callable 함수는 인자로 문자열 2개를 받으며, 첫 번쨰 문자열이 두 번째 문자열보다 순서가 낮은 경우 -1, 같은 경우 0, 높은 경우 1을 반환해야 한다.
- **iterdump()** : 연결된 DB의 내용을 SQL 질의 형태로 출력할 수 있는 이너레이터를 반환한다.

#### Attributes

- **isolation_level** : 트랜잭션의 격리 수준을 확인/설정한다.
  - None : Autocommit mode.
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

# Transaction Processing
conn.commit()

# Record Alignment
cur.execute('SELECT * FROM PhoneBook ORDER BY Name')
cur.execute('SELECT * FROM PhoneBook ORDER BY Name DESC')

def orderFunc(str1, str2):
    s1 = str1.upper()
    s2 = str2.upper()
    return (s1 > s2) - (s1 < s2)
conn.create_collation('hOrdering', orderFunc)
cur.execute('SELECT Name FROM PhoneBook ORDER BY Name COLLATE hOrdering')

# Aggregation
cur.execute('SELECT length(Name), upper(Name), lower(Name) FROM PhoneBook')
# Age integer라고 가정
cur.execute('SELECT max(Age), min(Age), sum(Age), FROM PhoneBook')
cur.execute('SELECT count(*), random(*) FROM PhoneBook')

class Average:
    def __init__(self):
        self.sum = 0
        self.cnt = 0
        
    def step(self, value):
        self.sum += value
        self.cnt += 1
        
    def finalize(self):
        return self.sum / self.cnt
conn.create_aggregate('hAvg', 1, Average)    
cur.execute('SELECT hAvg(Age) FROM PhoneBook')

# Datatype
cur.execute('CREATE TABLE testTable1(Name TEXT, Age INTEGER, Money REAL);')
cur.execute('CREATE TABLE testTable2(Name str, Age int, Money float);')

class Point(object):
    def __init__(self, x, y):
        self.x, self.y = x, y
        
	def __repr__(self):
        return "Point(%f, %f)" % (self.x, self.y)
def pointAdapter(point):
    return "%f:%f" % (point.x, point.y)
def pointConverter(s):
    x, y = list(map(float, s.decode().split(':')))
    return Point(x, y)
sqlite3.register_adapter(Point, pointAdapter)
sqlite3.register_converter('point', pointConverter)
p1 = Point(4, -3.2)
conn = sqlite3.connect(':memory:', detect_types=sqlite3.PARSE_DECLTYPES)
cur = conn.cursor()
cur.execute('create table test(p point)')
cur.execute('insert into test values (?)', (p, ))

# Make Dump
for l in conn.iterdump():
    print(l)

with open('dump.sql', 'w') as f:
    for l in conn.iterdump():
        f.write('{0}\n'.format(l))
```

&nbsp;

## Make Command-line Tool

```python
# pysqlite_command.py

# 표준 SQL 구문은 모두 수행 가능하며, 입력의 편의성을 위해 하나의 구문은 2줄 이상 연속으로 입력할 수 있게 함.
# SQL 구문의 종료는 ';'을 명시적으로 사용해야 하며, 한 번에 1개의 구문만 입력할 수 있게 함.
# SELECT 문에 대해서는 화면에 결과를 출력.
# 프로그램을 실행할 때 명시적으로 데이터베이스 파일을 지정하면 그 파일에 수행 결과를 저장.
# 데이터베이스 파일을 지정하지 않으면 메모리 내에서만 수행되고, 결과는 파일에 저장하지 않음.
# SQL 구문이 아닌 특수 명령어로 데이터베이스 덤프 기능을 지원하며, 파일과 화면으로 덤프된 내용이 출력 가능하도록 함.

import sqlite3
import sys
import re

if len(sys.argv) == 2:
    path = sys.argv[1]
else:
	path = ':memory:'
    
conn = sqlite3.connect(path)
conn.isolation_level = None
cur = conn.cursor()

buffer = ""

def PrintIntro():
    print("Usage")
    print("  -   help: .help;")
    
def PrintHelp():
    print(".dump\t\tDump DB")
    
def SQLDump(conn, file=None):
    if file != None:
        f = open(file, 'w')
	else:
        f = sys.stdout
        
	for l in conn.iterdump():
        f.write("{0}\n".format(l))
        
	if f != sys.stdout:
        f.close()

PrintIntro()

while True:
    line = input("pysqlite >> ")
    if buffer == "" and line == "":
        break
	buffer += line
    
    if sqlite3.complete_statement(buffer):
        buffer = buffer.strip()
        
        if buffer[0] == ".":
            cmd = re.sub('[ ;]', ' ', buffer).split()
            if cmd[0] == '.help':
         		PrintHelp()
			elif cmd[0] == '.dump':
                if len(cmd) == 2:
                    SQLDump(conn, cmd[1])
				else:
                    SQLDump(conn)
			else:
                try:
                    buffer = buffer.strip()
                   	cur.execute(buffer)
                    
                    if buffer.lstrip().upper().startswith("SELECT"):
                        print(cur.fetchall())
                        
				except sqlite3.Error as e:
                    print("Error: ", e.args[0])
				else:
                    print("Success")
			buffer = ""
conn.close()
print("Exit Program")
```

